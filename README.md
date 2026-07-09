<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Idil Abshir · Business Management</title>
  <!-- Font Awesome 6 -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Inter', 'Segoe UI', Roboto, system-ui, sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #0d1f16;
      padding: 2rem;
      position: relative;
      overflow-x: hidden;
    }

    /* moving background particles */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background: radial-gradient(circle at 20% 30%, rgba(212, 175, 55, 0.04) 0%, transparent 40%),
                  radial-gradient(circle at 80% 70%, rgba(120, 200, 130, 0.03) 0%, transparent 35%);
      pointer-events: none;
      z-index: 0;
      animation: bgDrift 25s infinite alternate ease-in-out;
    }

    @keyframes bgDrift {
      0% { transform: scale(1) rotate(0deg); opacity: 0.5; }
      100% { transform: scale(1.15) rotate(3deg); opacity: 1; }
    }

    /* main card */
    .profile-card {
      position: relative;
      max-width: 1300px;
      width: 100%;
      background: #1b3426;
      background: linear-gradient(145deg, #1b3426 0%, #142b1e 100%);
      border-radius: 48px;
      padding: 2.8rem;
      display: flex;
      flex-wrap: wrap;
      align-items: stretch;
      gap: 2rem;
      box-shadow: 0 40px 80px rgba(0, 0, 0, 0.8), 0 0 0 1px rgba(180, 210, 150, 0.06);
      border: 1px solid rgba(160, 200, 140, 0.08);
      z-index: 2;
      animation: cardFloat 6s infinite alternate ease-in-out;
    }

    @keyframes cardFloat {
      0% { transform: translateY(0px); }
      100% { transform: translateY(-6px); }
    }

    /* moving border */
    .profile-card::before {
      content: '';
      position: absolute;
      inset: -3px;
      border-radius: 50px;
      padding: 3px;
      background: conic-gradient(from 0deg, #b8d9a0, #d4af37, #7bbf7a, #b8d9a0, #d4af37, #7bbf7a, #b8d9a0);
      background-size: 300% 300%;
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: xor;
      mask-composite: exclude;
      animation: borderGlow 7s linear infinite;
      z-index: -1;
      pointer-events: none;
      opacity: 0.7;
    }

    @keyframes borderGlow {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    /* ----- LEFT PANEL : content ----- */
    .profile-left {
      flex: 2 1 480px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      color: #ecf5e8;
      order: 1;
      animation: slideInLeft 1s ease-out;
    }

    @keyframes slideInLeft {
      0% { opacity: 0; transform: translateX(-30px); }
      100% { opacity: 1; transform: translateX(0); }
    }

    /* ----- RIGHT PANEL : picture ----- */
    .profile-right {
      flex: 1 1 260px;
      min-width: 200px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 1.2rem;
      order: 2;
      animation: slideInRight 1s ease-out;
    }

    @keyframes slideInRight {
      0% { opacity: 0; transform: translateX(30px); }
      100% { opacity: 1; transform: translateX(0); }
    }

    .image-wrapper {
      position: relative;
      width: 100%;
      max-width: 280px;
      aspect-ratio: 1/1;
      border-radius: 40px;
      background: #2d5a3d;
      box-shadow: 0 20px 40px -8px rgba(0, 0, 0, 0.6), 0 0 0 2px rgba(180, 210, 150, 0.15);
      overflow: hidden;
      transition: transform 0.3s ease;
      border: 2px solid rgba(200, 220, 170, 0.1);
      animation: imagePulse 4s infinite alternate ease-in-out;
    }

    @keyframes imagePulse {
      0% { box-shadow: 0 20px 40px -8px rgba(0, 0, 0, 0.6), 0 0 0 2px rgba(180, 210, 150, 0.15); }
      100% { box-shadow: 0 25px 50px -8px rgba(0, 0, 0, 0.8), 0 0 0 4px rgba(212, 175, 55, 0.25); }
    }

    .image-wrapper img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
      animation: imgZoom 8s infinite alternate ease-in-out;
    }

    @keyframes imgZoom {
      0% { transform: scale(1); }
      100% { transform: scale(1.03); }
    }

    .image-wrapper:hover {
      transform: scale(1.01);
    }

    .badge {
      background: rgba(200, 220, 170, 0.06);
      backdrop-filter: blur(4px);
      padding: 0.4rem 1.6rem;
      border-radius: 60px;
      color: #cfe2c0;
      font-weight: 400;
      letter-spacing: 0.3px;
      border: 1px solid rgba(180, 210, 150, 0.08);
      display: inline-flex;
      align-items: center;
      gap: 10px;
      font-size: 0.85rem;
      animation: badgeGlow 3s infinite alternate ease-in-out;
    }

    @keyframes badgeGlow {
      0% { border-color: rgba(180, 210, 150, 0.08); }
      100% { border-color: rgba(212, 175, 55, 0.3); }
    }

    .badge i {
      color: #d4af37;
    }

    /* ----- NAME & TITLE with movement ----- */
    .profile-name {
      font-size: 3.6rem;
      font-weight: 700;
      letter-spacing: -0.02em;
      color: #f2faf0;
      line-height: 1.05;
      margin-bottom: 0.1rem;
      text-shadow: 0 2px 10px rgba(0,0,0,0.2);
      animation: nameGlow 3s infinite alternate ease-in-out;
    }

    @keyframes nameGlow {
      0% { text-shadow: 0 2px 10px rgba(0,0,0,0.2); }
      100% { text-shadow: 0 2px 20px rgba(212, 175, 55, 0.15); }
    }

    .profile-title {
      font-size: 1.1rem;
      font-weight: 400;
      color: #cde0c0;
      background: rgba(180, 210, 150, 0.05);
      display: inline-block;
      padding: 0.25rem 1.4rem;
      border-radius: 60px;
      backdrop-filter: blur(2px);
      margin-bottom: 1.2rem;
      border: 1px solid rgba(180, 210, 150, 0.06);
      letter-spacing: 0.2px;
      animation: titlePulse 2s infinite alternate ease-in-out;
    }

    @keyframes titlePulse {
      0% { opacity: 0.8; transform: scale(1); }
      100% { opacity: 1; transform: scale(1.02); }
    }

    .bio {
      font-size: 1rem;
      line-height: 1.7;
      color: #dceade;
      background: rgba(0, 0, 0, 0.12);
      backdrop-filter: blur(4px);
      padding: 1rem 1.6rem;
      border-radius: 28px;
      margin-bottom: 1.5rem;
      border-left: 6px solid #d4af37;
      box-shadow: inset 0 1px 4px rgba(255,255,255,0.02);
      animation: bioSlide 5s infinite alternate ease-in-out;
    }

    @keyframes bioSlide {
      0% { transform: translateX(0); }
      100% { transform: translateX(4px); }
    }

    .bio i {
      color: #d4af37;
      opacity: 0.8;
      margin-right: 6px;
    }

    /* ----- BUSINESS MANAGEMENT GRID (moving items) ----- */
    .management-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 12px;
      margin-bottom: 1.8rem;
      background: rgba(0, 0, 0, 0.08);
      backdrop-filter: blur(4px);
      padding: 1rem 1.2rem;
      border-radius: 32px;
      border: 1px solid rgba(180, 210, 150, 0.04);
    }

    .mgmt-item {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 400;
      color: #d4e6cc;
      font-size: 0.9rem;
      padding: 6px 8px;
      border-radius: 40px;
      background: rgba(212, 175, 55, 0.03);
      animation: itemFloat 4s infinite alternate ease-in-out;
      animation-delay: calc(var(--i, 0) * 0.2s);
    }

    .mgmt-item:nth-child(1) { --i: 0; }
    .mgmt-item:nth-child(2) { --i: 1; }
    .mgmt-item:nth-child(3) { --i: 2; }
    .mgmt-item:nth-child(4) { --i: 3; }
    .mgmt-item:nth-child(5) { --i: 4; }
    .mgmt-item:nth-child(6) { --i: 5; }
    .mgmt-item:nth-child(7) { --i: 6; }
    .mgmt-item:nth-child(8) { --i: 7; }
    .mgmt-item:nth-child(9) { --i: 8; }
    .mgmt-item:nth-child(10) { --i: 9; }

    @keyframes itemFloat {
      0% { transform: translateY(0px); opacity: 0.8; }
      100% { transform: translateY(-4px); opacity: 1; }
    }

    .mgmt-item i {
      color: #d4af37;
      font-size: 1rem;
      min-width: 20px;
      text-align: center;
      animation: iconSpin 6s infinite linear;
    }

    @keyframes iconSpin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .mgmt-item.highlight {
      background: rgba(212, 175, 55, 0.06);
      border: 1px solid rgba(212, 175, 55, 0.08);
    }

    /* project chips */
    .project-highlight {
      display: flex;
      flex-wrap: wrap;
      gap: 10px 16px;
      margin-bottom: 1.8rem;
      background: rgba(0, 0, 0, 0.06);
      backdrop-filter: blur(4px);
      padding: 0.6rem 1.4rem;
      border-radius: 60px;
      border: 1px solid rgba(180, 210, 150, 0.04);
      animation: projectSlide 7s infinite alternate ease-in-out;
    }

    @keyframes projectSlide {
      0% { padding-left: 1.4rem; }
      100% { padding-left: 2rem; }
    }

    .project-item {
      display: flex;
      align-items: center;
      gap: 8px;
      font-weight: 400;
      color: #d4e6cc;
      font-size: 0.9rem;
      animation: projectPulse 3s infinite alternate ease-in-out;
      animation-delay: calc(var(--p, 0) * 0.15s);
    }

    .project-item:nth-child(1) { --p: 0; }
    .project-item:nth-child(2) { --p: 1; }
    .project-item:nth-child(3) { --p: 2; }
    .project-item:nth-child(4) { --p: 3; }
    .project-item:nth-child(5) { --p: 4; }
    .project-item:nth-child(6) { --p: 5; }

    @keyframes projectPulse {
      0% { opacity: 0.7; transform: scale(1); }
      100% { opacity: 1; transform: scale(1.03); }
    }

    .project-item i {
      color: #d4af37;
      font-size: 0.95rem;
      animation: iconSpin 8s infinite linear;
    }

    .project-item.gold {
      background: rgba(212, 175, 55, 0.05);
      padding: 0 14px;
      border-radius: 40px;
    }

    /* ----- SOCIAL LINKS (moving on hover) ----- */
    .social-links {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      gap: 0.8rem 1.2rem;
      margin-top: 0.2rem;
      animation: socialAppear 1.2s ease-out;
    }

    @keyframes socialAppear {
      0% { opacity: 0; transform: translateY(20px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    .social-link {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      width: 50px;
      height: 50px;
      border-radius: 30px;
      background: rgba(255, 255, 255, 0.03);
      color: #e2efda;
      font-size: 1.3rem;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
      transition: all 0.25s cubic-bezier(0.2, 0.9, 0.4, 1.1);
      border: 1px solid rgba(180, 210, 150, 0.06);
      text-decoration: none;
      position: relative;
      backdrop-filter: blur(4px);
      animation: socialBounce 2s infinite alternate ease-in-out;
      animation-delay: calc(var(--s, 0) * 0.1s);
    }

    .social-link:nth-child(1) { --s: 0; }
    .social-link:nth-child(2) { --s: 1; }
    .social-link:nth-child(3) { --s: 2; }
    .social-link:nth-child(4) { --s: 3; }
    .social-link:nth-child(5) { --s: 4; }
    .social-link:nth-child(6) { --s: 5; }
    .social-link:nth-child(7) { --s: 6; }

    @keyframes socialBounce {
      0% { transform: translateY(0px); }
      100% { transform: translateY(-3px); }
    }

    .social-link:hover {
      transform: translateY(-6px) scale(1.05) !important;
      background: #d4af37;
      color: #0f2417;
      border-color: #d4af37;
      box-shadow: 0 12px 28px rgba(212, 175, 55, 0.25);
    }

    .social-link.whatsapp:hover { background: #25D366; color: #0f2417; border-color: #25D366; }
    .social-link.tiktok:hover { background: #ffffff; color: #0f2417; border-color: #fff; }
    .social-link.linkedin:hover { background: #0077b5; color: white; border-color: #0077b5; }
    .social-link.snapchat:hover { background: #FFFC00; color: #0f2417; border-color: #FFFC00; }
    .social-link.facebook:hover { background: #1877F2; color: white; border-color: #1877F2; }
    .social-link.instagram:hover { background: #d62976; color: white; border-color: #d62976; }

    .social-link::after {
      content: attr(data-label);
      position: absolute;
      bottom: -22px;
      left: 50%;
      transform: translateX(-50%) scale(0.8);
      background: #0f2417;
      color: #d4e6cc;
      font-size: 0.5rem;
      padding: 2px 10px;
      border-radius: 30px;
      opacity: 0;
      transition: 0.2s;
      white-space: nowrap;
      pointer-events: none;
      border: 1px solid rgba(180, 210, 150, 0.06);
    }
    .social-link:hover::after {
      opacity: 1;
      transform: translateX(-50%) scale(1);
    }

    .social-link-text {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: rgba(255, 255, 255, 0.02);
      backdrop-filter: blur(4px);
      padding: 0.3rem 1.2rem;
      border-radius: 60px;
      font-size: 0.8rem;
      font-weight: 400;
      color: #cde0c0;
      border: 1px solid rgba(180, 210, 150, 0.04);
      text-decoration: none;
      transition: all 0.2s;
      animation: textLinkPulse 3s infinite alternate ease-in-out;
    }

    @keyframes textLinkPulse {
      0% { opacity: 0.7; }
      100% { opacity: 1; }
    }

    .social-link-text:hover {
      background: #d4af37;
      color: #0f2417;
      transform: translateY(-2px);
    }

    /* responsive */
    @media (max-width: 850px) {
      .profile-card {
        flex-direction: column-reverse;
        padding: 2rem;
        border-radius: 40px;
      }
      .profile-left { order: 2; }
      .profile-right { order: 1; }
      .image-wrapper {
        max-width: 200px;
      }
      .profile-name {
        font-size: 2.8rem;
      }
      .management-grid {
        grid-template-columns: repeat(auto-fit, minmax(130px, 1fr));
      }
    }

    @media (max-width: 480px) {
      .profile-card { padding: 1.4rem; }
      .profile-name { font-size: 2.2rem; }
      .social-link { width: 44px; height: 44px; font-size: 1.1rem; }
      .management-grid { grid-template-columns: 1fr 1fr; }
    }
  </style>
</head>
<body>
  <div class="profile-card">
    <!-- LEFT: content -->
    <div class="profile-left">
      <h1 class="profile-name">Idil Abshir</h1>
      <div class="profile-title">
        <i class="fas fa-briefcase" style="margin-right: 6px; color: #d4af37;"></i> 
        MSc Business Management · Strategy & Operations
      </div>

      <div class="bio">
        <i class="fas fa-quote-left"></i> 
        Business leader with 7+ years driving transformation across finance, retail, and ESG. 
        Expert in operational efficiency, project governance, and data-driven decision making.
        <span style="display:block; margin-top: 0.3rem; font-weight:300; font-size:0.9rem; opacity:0.8;">
          <i class="fas fa-check-circle" style="color: #d4af37;"></i> 15+ projects · 5 industries · 3 continents
        </span>
      </div>

      <!-- Business Management: what she does -->
      <div class="management-grid">
        <span class="mgmt-item"><i class="fas fa-chart-pie"></i> Strategic Planning</span>
        <span class="mgmt-item"><i class="fas fa-people-group"></i> Team Leadership</span>
        <span class="mgmt-item"><i class="fas fa-bullseye"></i> Performance Mgmt</span>
        <span class="mgmt-item highlight"><i class="fas fa-hand-holding-dollar"></i> Financial Analysis</span>
        <span class="mgmt-item"><i class="fas fa-arrow-trend-up"></i> Growth Strategy</span>
        <span class="mgmt-item"><i class="fas fa-gears"></i> Process Optimization</span>
        <span class="mgmt-item"><i class="fas fa-scale-balanced"></i> Risk Governance</span>
        <span class="mgmt-item highlight"><i class="fas fa-robot"></i> Digital Transformation</span>
        <span class="mgmt-item"><i class="fas fa-handshake"></i> Stakeholder Relations</span>
        <span class="mgmt-item"><i class="fas fa-cloud"></i> Change Management</span>
      </div>

      <!-- project chips -->
      <div class="project-highlight">
        <span class="project-item"><i class="fas fa-rocket"></i> Fintech · 2025</span>
        <span class="project-item"><i class="fas fa-chart-line"></i> Retail expansion</span>
        <span class="project-item"><i class="fas fa-globe"></i> ESG strategy</span>
        <span class="project-item"><i class="fas fa-cloud"></i> Digital ops</span>
        <span class="project-item gold"><i class="fas fa-seedling"></i> Green transition</span>
        <span class="project-item"><i class="fas fa-microchip"></i> AI integration</span>
      </div>

      <!-- social links -->
      <div class="social-links">
        <a href="#" class="social-link whatsapp" data-label="WhatsApp" target="_blank"><i class="fab fa-whatsapp"></i></a>
        <a href="https://www.tiktok.com/@nawaal4090?_r=1&_d=emm0c3d9l52ad4&sec_uid=MS4wLjABAAAAb7Zeq0mBp679htnS_VfmfKgEKbNdoiyfL0jugaVTdXE7JquchPOL7GwjrczmxjiL&share_author_id=6939573120093832198&sharer_language=en&source=h5_m&u_code=dhf663f855k46b&item_author_type=1&utm_source=copy&tt_from=copy&enable_checksum=1&utm_medium=ios&share_link_id=BBFFDEEA-B2EA-492C-A3DC-7E4A5697919A&user_id=6939573120093832198&sec_user_id=MS4wLjABAAAAb7Zeq0mBp679htnS_VfmfKgEKbNdoiyfL0jugaVTdXE7JquchPOL7GwjrczmxjiL&social_share_type=4&ug_btm=b8727,b0&utm_campaign=client_share&share_app_id=1233" class="social-link tiktok" data-label="TikTok" target="_blank"><i class="fab fa-tiktok"></i></a>
        <a href="https://www.linkedin.com/in/idil-abshir-368396209?utm_source=share_via&utm_content=profile&utm_medium=member_ios" class="social-link linkedin" data-label="LinkedIn" target="_blank"><i class="fab fa-linkedin-in"></i></a>
        <a href="https://www.snapchat.com/add/idilabshir2024?share_id=tA28NqbvSk-ZjNhZwfmOAg&locale=en_GB" class="social-link snapchat" data-label="Snapchat" target="_blank"><i class="fab fa-snapchat-ghost"></i></a>
        <a href="https://www.facebook.com/share/14ge1wFArGX/?mibextid=wwXIfr" class="social-link facebook" data-label="Facebook" target="_blank"><i class="fab fa-facebook-f"></i></a>
        <a href="https://www.instagram.com/idilabshi?igsh=aTNiYWFrdTRnc2d5&utm_source=qr" class="social-link instagram" data-label="Instagram" target="_blank"><i class="fab fa-instagram"></i></a>
        <a href="#" class="social-link-text"><i class="fas fa-envelope" style="color: #d4af37;"></i> idil@business.com</a>
      </div>
    </div>

    <!-- RIGHT: picture -->
    <div class="profile-right">
      <div class="image-wrapper">
        <!-- ★★★ REPLACE "your-picture.jpg" WITH YOUR IMAGE ★★★ -->
        <img src="your-name.png" alt="Idil Abshir" 
             onerror="this.onerror=null; this.src='data:image/svg+xml,%3Csvg xmlns=%22http://www.w3.org/2000/svg%22 width=%22400%22 height=%22400%22 viewBox=%220 0 400 400%22%3E%3Crect width=%22400%22 height=%22400%22 fill=%22%232d5a3d%22/%3E%3Ctext x=%2250%25%22 y=%2245%25%22 font-size=%2280%22 font-family=%22Arial%22 fill=%22%23d4e6cc%22 text-anchor=%22middle%22 dominant-baseline=%22central%22%3E👩🏾%3C/text%3E%3Ctext x=%2250%25%22 y=%2272%25%22 font-size=%2222%22 font-family=%22Segoe UI, sans-serif%22 fill=%22%23bdd6b0%22 text-anchor=%22middle%22%3EIdil Abshir%3C/text%3E%3C/svg%3E';">
      </div>
      <div class="badge">
        <i class="fas fa-award"></i> <span>MSc · Business</span> 
        <i class="fas fa-check-circle" style="color: #d4af37;"></i>
      </div>
      <div class="badge" style="background: rgba(212, 175, 55, 0.05); border-color: rgba(212, 175, 55, 0.1);">
        <i class="fas fa-star" style="color: #d4af37;"></i> PMP · Lean Six Sigma
      </div>
    </div>
  </div>
</body>
</html>
