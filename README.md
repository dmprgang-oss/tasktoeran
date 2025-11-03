import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView
import android.widget.Toast
import com.google.firebase.auth.FirebaseAuth
import com.google.firebase.firestore.FirebaseFirestore

class DashboardActivity : AppCompatActivity() {

    // Firebase instance à¦—à§à¦²à§‹ declare à¦•à¦°à§à¦¨
    private lateinit var auth: FirebaseAuth
    private lateinit var db: FirebaseFirestore

    // UI elements declare à¦•à¦°à§à¦¨
    private lateinit var tvUserName: TextView
    private lateinit var tvBalance: TextView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_dashboard) // à¦†à¦ªà¦¨à¦¾à¦° dashboard XML à¦«à¦¾à¦‡à¦²

        // Instance à¦—à§à¦²à§‹ initialize à¦•à¦°à§à¦¨
        auth = FirebaseAuth.getInstance()
        db = FirebaseFirestore.getInstance()

        // UI elements à¦—à§à¦²à§‹à¦•à§‡ à¦¤à¦¾à¦¦à§‡à¦° ID à¦¦à¦¿à§Ÿà§‡ à¦¯à§à¦•à§à¦¤ à¦•à¦°à§à¦¨
        tvUserName = findViewById(R.id.tvUserName)
        tvBalance = findViewById(R.id.tvBalance)

        // à¦¬à§à¦¯à¦¬à¦¹à¦¾à¦°à¦•à¦¾à¦°à§€à¦° à¦¤à¦¥à§à¦¯ à¦²à§‹à¦¡ à¦•à¦°à¦¾à¦° à¦œà¦¨à§à¦¯ à¦«à¦¾à¦‚à¦¶à¦¨ à¦•à¦² à¦•à¦°à§à¦¨
        loadUserProfile()
    }

    private fun loadUserProfile() {
        // à¦¬à¦°à§à¦¤à¦®à¦¾à¦¨à§‡ à¦²à¦—à¦‡à¦¨ à¦¥à¦¾à¦•à¦¾ à¦¬à§à¦¯à¦¬à¦¹à¦¾à¦°à¦•à¦¾à¦°à§€à¦•à§‡ à¦ªà¦¾à¦¨
        val currentUser = auth.currentUser

        if (currentUser != null) {
            val userId = currentUser.uid

            // Firestore à¦¥à§‡à¦•à§‡ à¦¬à§à¦¯à¦¬à¦¹à¦¾à¦°à¦•à¦¾à¦°à§€à¦° à¦¡à¦•à§à¦®à§‡à¦¨à§à¦Ÿ à¦ªà¦¾à¦¨
            val userDocRef = db.collection("Users").document(userId)

            userDocRef.get()
                .addOnSuccessListener { document ->
                    if (document != null && document.exists()) {
                        // à¦¡à¦•à§à¦®à§‡à¦¨à§à¦Ÿ à¦¥à§‡à¦•à§‡ à¦¨à¦¾à¦® à¦à¦¬à¦‚ à¦¬à§à¦¯à¦¾à¦²à§‡à¦¨à§à¦¸ à¦ªà¦¾à¦¨
                        val userName = document.getString("name")
                        val balance = document.getDouble("balance")

                        // UI à¦¤à§‡ à¦¨à¦¾à¦® à¦à¦¬à¦‚ à¦¬à§à¦¯à¦¾à¦²à§‡à¦¨à§à¦¸ à¦¸à§‡à¦Ÿ à¦•à¦°à§à¦¨
                        tvUserName.text = userName ?: "User Name" // à¦¯à¦¦à¦¿ à¦¨à¦¾à¦® à¦¨à¦¾ à¦¥à¦¾à¦•à§‡, à¦¤à¦¾à¦¹à¦²à§‡ "User Name" à¦¦à§‡à¦–à¦¾à¦¬à§‡
                        tvBalance.text = "à§³ ${String.format("%.2f", balance ?: 0.00)}"

                    } else {
                        // à¦¯à¦¦à¦¿ à¦•à§‹à¦¨à§‹ à¦•à¦¾à¦°à¦£à§‡ à¦¬à§à¦¯à¦¬à¦¹à¦¾à¦°à¦•à¦¾à¦°à§€à¦° à¦¤à¦¥à§à¦¯ à¦¡à¦¾à¦Ÿà¦¾à¦¬à§‡à¦¸à§‡ à¦¨à¦¾ à¦ªà¦¾à¦“à§Ÿà¦¾ à¦¯à¦¾à§Ÿ
                        Toast.makeText(this, "User data not found.", Toast.LENGTH_SHORT).show()
                    }
                }
                .addOnFailureListener { exception ->
                    // à¦¯à¦¦à¦¿ à¦¡à¦¾à¦Ÿà¦¾à¦¬à§‡à¦¸ à¦¥à§‡à¦•à§‡ à¦¤à¦¥à§à¦¯ à¦†à¦¨à¦¤à§‡ à¦•à§‹à¦¨à§‹ à¦¸à¦®à¦¸à§à¦¯à¦¾ à¦¹à§Ÿ
                    Toast.makeText(this, "Error fetching data: ${exception.message}", Toast.LENGTH_SHORT).show()
                }
        } else {
            // à¦¯à¦¦à¦¿ à¦•à§‹à¦¨à§‹ à¦¬à§à¦¯à¦¬à¦¹à¦¾à¦°à¦•à¦¾à¦°à§€ à¦²à¦—à¦‡à¦¨ à¦•à¦°à¦¾ à¦¨à¦¾ à¦¥à¦¾à¦•à§‡
            // à¦¤à¦¾à¦•à§‡ à¦²à¦—à¦‡à¦¨ à¦ªà§‡à¦œà§‡ à¦ªà¦¾à¦ à¦¿à§Ÿà§‡ à¦¦à¦¿à¦¨
            // startActivity(Intent(this, LoginActivity::class.java))
            // finish()
        }
    }
}
