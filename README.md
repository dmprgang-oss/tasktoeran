<!doctype html>
<html lang="bn">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>ড্যাশবোর্ড - ডিজিটাল স্টাইল</title>
  <style>
    :root{
      --bg:#dff6f4;
      --card:#ffffff;
      --accent:#3fc28b;
      --muted:#6b7f7a;
      --shadow: 0 6px 18px rgba(15,40,40,0.08);
      --rounded:16px;
      font-family: "Noto Sans Bengali", "Segoe UI", Roboto, Arial, sans-serif;
    }
    html,body{height:100%; margin:0; background:linear-gradient(180deg,#c8f0ec 0%, #e8fbf8 60%); color:#0b2b27;}
    .app {
      min-height:100vh;
      display:flex;
      flex-direction:column;
      box-sizing:border-box;
    }

    /* Top bar */
    .topbar{
      padding:18px 16px 8px;
      display:flex;
      align-items:center;
      gap:12px;
    }
    .brand {
      font-weight:700;
      font-size:20px;
      color:#083b32;
      flex:1;
      text-align:center;
    }
    .searchbar{
      margin:0 12px;
      display:flex;
      gap:8px;
      align-items:center;
      width:100%;
    }
    .url {
      background:linear-gradient(180deg, #eafaf7, #ffffff);
      border-radius:28px;
      padding:10px 14px;
      box-shadow:var(--shadow);
      display:flex;
      align-items:center;
      gap:10px;
      width:100%;
    }
    .url svg{opacity:.85}
    .no-inet{
      text-align:center;
      font-size:12px;
      color:#758d8a;
      margin-top:-4px;
    }

    /* Heading */
    .heading{
      text-align:center;
      font-size:24px;
      font-weight:700;
      margin:18px 0 10px;
      color:#0c5046;
    }

    /* Grid */
    .grid{
      padding: 0 12px 92px; /* leave space for bottom nav */
      display:grid;
      grid-template-columns: repeat(3, 1fr);
      gap:12px;
    }
    .card{
      background:var(--card);
      border-radius:14px;
      padding:16px;
      box-shadow:var(--shadow);
      display:flex;
      flex-direction:column;
      align-items:center;
      gap:8px;
      min-height:96px;
      justify-content:center;
      text-align:center;
      cursor:pointer;
      transition:transform .12s ease, box-shadow .12s ease;
    }
    .card:active{transform:translateY(2px)}
    .card .icon{
      width:36px;
      height:36px;
      display:flex;
      align-items:center;
      justify-content:center;
    }
    .card .label{
      font-size:13px;
      color:var(--muted);
      font-weight:600;
    }
    /* Highlighted card (like selected) */
    .card.highlight{
      background:linear-gradient(180deg,#e6faf3,#dff6ef);
    }

    /* Bottom nav */
    .bottom-nav{
      position:fixed;
      left:12px;
      right:12px;
      bottom:12px;
      height:64px;
      background:linear-gradient(90deg,#43bf82,#26a66a);
      border-radius:14px;
      box-shadow:0 8px 30px rgba(7,70,50,0.18);
      display:flex;
      align-items:center;
      justify-content:space-around;
      padding:0 8px;
      color:#fff;
      z-index:40;
    }
    .nav-item{
      display:flex;
      flex-direction:column;
      align-items:center;
      gap:4px;
      font-size:12px;
      text-decoration:none;
      color:rgba(255,255,255,0.95);
      opacity:.95;
    }
    .nav-item svg{width:22px;height:22px;opacity:.95}
    .nav-item .label{font-size:12px}

    /* Responsive */
    @media (max-width:420px){
      .grid{grid-template-columns: repeat(3, 1fr);}
      .brand{font-size:18px}
    }
    @media (max-width:360px){
      .grid{grid-template-columns: repeat(2, 1fr);}
    }
  </style>
</head>
<body>
  <div class="app">
    <div class="topbar">
      <div style="width:36px;height:36px;border-radius:10px;background:#fff;box-shadow:var(--shadow);display:flex;align-items:center;justify-content:center">
        <!-- hamburger -->
        <svg width="18" height="14" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="3" y="5" width="18" height="2" rx="1" fill="#0b2b27"/>
          <rect x="3" y="11" width="18" height="2" rx="1" fill="#0b2b27"/>
          <rect x="3" y="17" width="18" height="2" rx="1" fill="#0b2b27"/>
        </svg>
      </div>

      <div class="brand">ডিজিটাল-আর্ন</div>

      <div style="width:36px;height:36px;border-radius:10px;background:#fff;box-shadow:var(--shadow);display:flex;align-items:center;justify-content:center">
        <!-- plus -->
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 5v14M5 12h14" stroke="#0b2b27" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
    </div>

    <div class="no-inet">No internet connection</div>

    <div class="heading">আমাদের প্রজেক্ট সমূহ</div>

    <div class="grid" id="grid">
      <!-- Row of cards (12 sample items) -->
      <div class="card">
        <div class="icon">
          <!-- briefcase icon -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="3" y="8" width="18" height="11" rx="2" stroke="#14a082" stroke-width="1.6" fill="#e9fff6"/>
            <path d="M9 8V6a3 3 0 0 1 3-3h0a3 3 0 0 1 3 3v2" stroke="#14a082" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <div class="label">মাইক্রো টাস্ক</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- mail -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="3" y="5" width="18" height="14" rx="2" stroke="#e44aa6" stroke-width="1.6" fill="#fff0f7"/>
            <path d="M21 7l-9 6L3 7" stroke="#e44aa6" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>
        <div class="label">জিমেইল সেল</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- facebook circle -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="12" cy="12" r="9" stroke="#2b6fb5" stroke-width="1.6" fill="#eef6ff"/>
            <path d="M13 8.5h1.5V11H13v6h-2v-6H9.5V9.5H11V8c0-1.1.9-2 2-2h1v2.5h-1c-.28 0-.5.22-.5.5V8.5z" fill="#2b6fb5"/>
          </svg>
        </div>
        <div class="label">ফেসবুক সেল</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- refer users -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="8.5" cy="9.5" r="2.3" stroke="#10a6b0" stroke-width="1.5" fill="#eaffff"/>
            <circle cx="16" cy="9.5" r="2.3" stroke="#10a6b0" stroke-width="1.5" fill="#eaffff"/>
            <path d="M5 16c1.6-2 4-3 7-3s5.4 1 7 3" stroke="#10a6b0" stroke-width="1.4" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="label">রেফার করুন</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- target -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <circle cx="12" cy="12" r="7" stroke="#d84b4b" stroke-width="1.5" fill="#fff5f5"/>
            <circle cx="12" cy="12" r="3" stroke="#d84b4b" stroke-width="1.5" fill="#fff5f5"/>
            <path d="M12 3v2M12 19v2M3 12h2M19 12h2" stroke="#d84b4b" stroke-width="1.4" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="label">টার্গেট বোনাস</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- wallet -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="3" y="6" width="18" height="12" rx="2" stroke="#0b8a58" stroke-width="1.6" fill="#f0fff7"/>
            <path d="M17 11h1a1 1 0 0 1 0 2h-1" stroke="#0b8a58" stroke-width="1.6" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="label">মাসিক বেতন</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- trophy -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M8 3h8v3a4 4 0 0 1-4 4 4 4 0 0 1-4-4V3z" stroke="#d3852d" stroke-width="1.5" fill="#fff6e9"/>
            <path d="M9 16h6v3H9z" stroke="#d3852d" stroke-width="1.3" fill="#fff6e9"/>
          </svg>
        </div>
        <div class="label">লিডারবোর্ড</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- recharge -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="6" y="5" width="12" height="14" rx="2" stroke="#d67b28" stroke-width="1.5" fill="#fff6ea"/>
            <rect x="10" y="9" width="4" height="3" rx="0.6" fill="#d67b28"/>
          </svg>
        </div>
        <div class="label">মোবাইল রিচার্জ</div>
      </div>

      <div class="card highlight">
        <div class="icon">
          <!-- flow/offer -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M6 12h12M12 6v12" stroke="#6e5bd8" stroke-width="1.6" stroke-linecap="round"/>
            <rect x="3" y="3" width="18" height="18" rx="4" stroke="#6e5bd8" stroke-width="1.2" fill="#f0eeff"/>
          </svg>
        </div>
        <div class="label">ড্রাইভ অফার</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- gem -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 3l3.5 6-3.5 5-3.5-5L12 3z" stroke="#9b55e0" stroke-width="1.3" fill="#fbf7ff"/>
            <path d="M3 18l9-3 9 3-9 3-9-3z" stroke="#9b55e0" stroke-width="1.1" fill="#fbf7ff"/>
          </svg>
        </div>
        <div class="label">প্রিমিয়াম সার্ভিস</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- instagram -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="3" y="3" width="18" height="18" rx="5" stroke="#e879a3" stroke-width="1.6" fill="#fff2f7"/>
            <circle cx="12" cy="12" r="3" stroke="#e879a3" stroke-width="1.6" fill="#fff2f7"/>
            <circle cx="17.5" cy="6.5" r="0.6" fill="#e879a3"/>
          </svg>
        </div>
        <div class="label">ইনস্টাগ্রাম সেল</div>
      </div>

      <div class="card">
        <div class="icon">
          <!-- telegram -->
          <svg viewBox="0 0 24 24" width="36" height="36" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M21 4L3 10l5.5 2.2L9 21l4-3 4 3-1.6-8.8L21 4z" stroke="#17a07a" stroke-width="1.2" fill="#ecfff6"/>
          </svg>
        </div>
        <div class="label">টেলিগ্রাম সেল</div>
      </div>
    </div>

    <!-- bottom nav -->
    <nav class="bottom-nav" aria-label="Bottom navigation">
      <a class="nav-item" href="#" onclick="navClick('home'); return false;">
        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M3 11.6L12 4l9 7.6V20a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1V11.6z" stroke="#fff" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/></svg>
        <span class="label">হোম</span>
      </a>

      <a class="nav-item" href="#" onclick="navClick('team'); return false;">
        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M17 21v-2a4 4 0 0 0-4-4H9a4 4 0 0 0-4 4v2" stroke="#fff" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/><circle cx="12" cy="7" r="4" stroke="#fff" stroke-width="1.4"/></svg>
        <span class="label">মাই টিম</span>
      </a>

      <a class="nav-item" href="#" onclick="navClick('earn'); return false;">
        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12 8v8M8 12h8" stroke="#fff" stroke-width="1.6" stroke-linecap="round"/></svg>
        <span class="label">ইনকাম</span>
      </a>

      <a class="nav-item" href="#" onclick="navClick('support'); return false;">
        <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M18 8a6 6 0 1 0-12 0v3a6 6 0 0 0 6 6" stroke="#fff" stroke-width="1.4" stroke-linecap="round" stroke-linejoin="round"/><path d="M12 19v2" stroke="#fff" stroke-width="1.4" stroke-linecap="round"/></svg>
        <span class="label">সাপোর্ট</span>
      </a>
    </nav>
  </div>

  <script>
    // Simple interactions: click handler for demo
    function navClick(id){
      alert({
        home: 'হোম ট্যাব',
        team: 'মাই টিম',
        earn: 'ইনকাম',
        support: 'সাপোর্ট'
      }[id] + ' ক্লিক করা হয়েছে। (Demo)');
    }

    // Demo: each card click
    document.querySelectorAll('.card').forEach((c, idx)=>{
      c.addEventListener('click', ()=>{
        c.classList.add('highlight');
        setTimeout(()=>c.classList.remove('highlight'), 600);
      })
    })
  </script>
</body>
</html>
