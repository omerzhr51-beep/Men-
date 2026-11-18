<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Lokanta Menüsü</title>
<style>
  :root{
    --bg:#0d0d0d; --card:#181818; --card2:#242424; --accent:#ffffff;
    --text:#f5f5f5; --muted:#9e9e9e; --green:#4caf50; --red:#e53935; --blue:#42a5f5;
  }
  *{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',Tahoma,sans-serif}
  body{background:var(--bg);color:var(--text);min-height:100vh;overflow-x:hidden}
  header{background:#000;border-bottom:2px solid #2e2e2e;position:sticky;top:0;z-index:10}
  .header-in{max-width:960px;margin:auto;display:flex;align-items:center;justify-content:space-between;padding:14px 18px;flex-wrap:wrap;gap:8px}
  .logo{font-size:22px;font-weight:800;color:var(--accent);letter-spacing:1px}
  .badge{padding:5px 12px;border-radius:20px;font-size:12px;font-weight:700}
  .open{background:#142e14;color:#81c784;border:1px solid #2e7d32}
  .closed{background:#2e1414;color:#e57373;border:1px solid #c62828}
  nav{max-width:960px;margin:auto;display:flex;gap:6px;padding:10px 18px;flex-wrap:wrap;border-top:1px solid #1a1a1a}
  nav a{color:var(--muted);text-decoration:none;padding:6px 12px;border-radius:8px;font-size:14px;transition:.2s}
  nav a:hover,nav a.act{background:var(--card2);color:var(--accent);font-weight:600}
  main{max-width:960px;margin:auto;padding:20px 16px 80px}
  .hero{text-align:center;padding:24px 10px 18px}
  .hero h1{font-size:30px;color:var(--accent);margin-bottom:6px}
  .hero p{color:var(--muted);font-size:14.5px}
  .hours-box{background:var(--card);border:1px solid #2e2e2e;border-radius:10px;padding:10px 18px;display:inline-block;margin-top:12px;font-size:14px}

  /* Arama Kutusu */
  .search-box{margin:14px 0 6px}
  .search-box input{background:var(--card);border:1px solid #333;padding:11px 14px;border-radius:10px;color:#fff;width:100%;font-size:14px;margin:0}

  .cat-bar{display:flex;gap:8px;overflow-x:auto;padding:10px 0 16px;scrollbar-width:none}
  .cat-bar::-webkit-scrollbar{display:none}
  .cat-pill{background:var(--card);color:var(--muted);border:1px solid #333;padding:7px 14px;border-radius:20px;font-size:13px;white-space:nowrap;cursor:pointer;transition:.2s}
  .cat-pill.active,.cat-pill:hover{background:#fff;color:#000;font-weight:700;border-color:#fff}

  .specials{background:var(--card);border:1px dashed #444;padding:14px;border-radius:12px;margin-bottom:18px;text-align:center}
  .specials h3{color:var(--accent);margin-bottom:4px;font-size:15px}
  .specials p{color:var(--muted);font-size:13.5px}

  .cat-title{margin:26px 0 12px;font-size:19px;color:var(--accent);border-left:4px solid var(--accent);padding-left:10px;font-weight:700}
  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:14px}
  .item{background:var(--card);border:1px solid #2a2a2a;border-radius:12px;overflow:hidden;transition:.2s;display:flex;flex-direction:column}
  .item:hover{border-color:#666;transform:translateY(-2px)}
  .item.off{opacity:.4}
  .item-img{width:100%;height:160px;background:#222;object-fit:cover}
  .item-content{padding:14px;flex:1;display:flex;flex-direction:column;justify-content:space-between}
  .item h3{font-size:16px;margin-bottom:6px;display:flex;justify-content:space-between;align-items:flex-start;gap:8px;color:var(--accent)}
  .price{color:var(--accent);font-weight:800;font-size:17px;white-space:nowrap;background:#262626;padding:2px 8px;border-radius:6px}
  .item p{color:var(--muted);font-size:13px;line-height:1.45}
  .tag{font-size:10px;background:#3a1818;border:1px solid #c62828;color:#ff8a80;padding:2px 6px;border-radius:6px;margin-left:6px;vertical-align:middle}

  .team{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:14px}
  .member{background:var(--card);border:1px solid #2e2e2e;border-radius:12px;padding:20px;text-align:center}
  .avatar{width:60px;height:60px;border-radius:50%;background:#2e2e2e;border:1px solid #555;display:flex;align-items:center;justify-content:center;font-size:24px;font-weight:800;color:#fff;margin:0 auto 10px}
  .member h4{margin-bottom:4px;color:var(--accent)}
  .member span{color:var(--muted);font-size:13px}

  .contact-card{background:var(--card);border:1px solid #2e2e2e;border-radius:12px;padding:22px;max-width:600px;margin:auto}
  .contact-item{display:flex;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid #262626;font-size:15px}
  .contact-item:last-child{border-bottom:none}
  .call-btn{display:block;width:100%;text-align:center;background:#fff;color:#000;font-weight:700;padding:12px;border-radius:8px;text-decoration:none;margin-top:16px}

  footer{text-align:center;color:var(--muted);font-size:12.5px;padding:20px;border-top:1px solid #1f1f1f}

  /* Panel */
  .panel-wrap{max-width:740px;margin:16px auto;background:var(--card);border:1px solid #2e2e2e;border-radius:14px;padding:20px}
  .panel-wrap h2{color:var(--accent);margin-bottom:16px;font-size:20px}
  input,select,textarea{width:100%;padding:10px 12px;border-radius:8px;border:1px solid #3d3d3d;background:var(--card2);color:var(--text);font-size:14px;margin-bottom:12px}
  input[type="file"]{padding:8px;background:#1c1c1c;cursor:pointer}
  label{font-size:12.5px;color:var(--muted);display:block;margin-bottom:4px}
  .btn{background:#fff;color:#000;border:none;padding:10px 16px;border-radius:8px;font-weight:700;cursor:pointer;font-size:13.5px;transition:.2s}
  .btn:hover{background:#d4d4d4}
  .btn.sec{background:#333;color:var(--text)}
  .btn.edt{background:#2196f3;color:#fff}
  .btn.dng{background:var(--red);color:#fff}
  .btn.sm{padding:6px 10px;font-size:12px}
  .row{display:flex;gap:10px;flex-wrap:wrap}
  .row>*{flex:1;min-width:130px}

  /* Mobil Uyumlu Admin Yemek Kartları */
  .admin-list{display:flex;flex-direction:column;gap:10px}
  .admin-card{background:var(--card2);border:1px solid #353535;border-radius:10px;padding:12px;display:flex;flex-direction:column;gap:10px}
  .admin-top{display:flex;align-items:center;gap:12px}
  .thumb{width:54px;height:54px;border-radius:8px;object-fit:cover;background:#181818;flex-shrink:0}
  .admin-info{flex:1;min-width:0}
  .admin-info h4{font-size:15px;color:#fff;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
  .admin-info span{font-size:12px;color:var(--muted)}
  .admin-actions{display:flex;gap:6px;flex-wrap:wrap;align-items:center;border-top:1px solid #333;padding-top:10px}
  .price-input{width:85px!important;margin:0!important;padding:6px 8px!important;font-weight:700;text-align:center}

  /* Düzenleme Modalı */
  .modal-bg{position:fixed;inset:0;background:rgba(0,0,0,.85);z-index:50;display:flex;align-items:center;justify-content:center;padding:16px}
  .modal{background:var(--card);border:1px solid #444;border-radius:14px;padding:20px;width:100%;max-width:480px;max-height:90vh;overflow-y:auto}
  .modal h3{margin-bottom:14px;color:#fff;display:flex;justify-content:space-between;align-items:center}

  .preview-box{width:100%;max-height:150px;object-fit:cover;border-radius:8px;margin-bottom:12px;border:1px solid #444;display:none}
  .msg{padding:10px 14px;border-radius:8px;margin-bottom:12px;font-size:13.5px}
  .ok{background:#142e14;color:#81c784;border:1px solid #2e7d32}
  .err{background:#2e1414;color:#e57373;border:1px solid #c62828}
  .hidden{display:none!important}
  .tabs{display:flex;gap:6px;margin-bottom:16px;flex-wrap:wrap}
  .tabs button{background:var(--card2);color:var(--muted);border:1px solid #3d3d3d;padding:8px 12px;border-radius:8px;cursor:pointer;font-size:13px}
  .tabs button.on{background:#fff;color:#000;font-weight:700;border-color:#fff}
  .logout{float:right;font-size:12px;color:var(--muted);cursor:pointer;text-decoration:underline}
  .lock-link{position:fixed;bottom:16px;right:16px;background:var(--card2);border:1px solid #444;color:var(--accent);width:44px;height:44px;border-radius:50%;font-size:18px;cursor:pointer;display:flex;align-items:center;justify-content:center;text-decoration:none;box-shadow:0 4px 12px rgba(0,0,0,.6)}
</style>
</head>
<body>

<header>
  <div class="header-in">
    <div class="logo" id="logoText">🍽️ Lezzet Lokantası</div>
    <div id="statusBadge" class="badge open">—</div>
  </div>
  <nav>
    <a href="#anasayfa" data-nav="anasayfa">Menü</a>
    <a href="#ekip" data-nav="ekip">Ekibimiz</a>
    <a href="#iletisim" data-nav="iletisim">İletişim & Konum</a>
    <a href="#panel" data-nav="panel" style="margin-left:auto">🔐 Yönetim</a>
  </nav>
</header>

<main>
  <!-- ANASAYFA -->
  <section id="v-anasayfa">
    <div class="hero">
      <h1 id="heroTitle">Lezzet Lokantası</h1>
      <p>Günlük taze ev yemekleri, çorbalar, ızgaralar ve tatlılar</p>
      <div class="hours-box">🕒 Açık Saatler: <b id="hoursText">—</b></div>
    </div>

    <div class="specials">
      <h3>🌟 Günün Menüsü & Tavsiyesi</h3>
      <p id="specialText">—</p>
    </div>

    <div class="search-box">
      <input type="text" id="menuSearch" placeholder="🔍 Menüde yemek ara (örn. mercimek, kebap, sütlaç)..." oninput="renderMenu()">
    </div>

    <div class="cat-bar" id="catBar"></div>
    <div id="menuArea"></div>
  </section>

  <!-- EKIP -->
  <section id="v-ekip" class="hidden">
    <div class="hero"><h1>Ustalarımız & Ekibimiz</h1><p>Lezzeti size ulaştıran kadromuz</p></div>
    <div class="team" id="teamArea"></div>
  </section>

  <!-- ILETISIM -->
  <section id="v-iletisim" class="hidden">
    <div class="hero"><h1>İletişim & Adres</h1></div>
    <div class="contact-card">
      <div class="contact-item"><span>📍</span><span id="infoAddress">—</span></div>
      <div class="contact-item"><span>📞</span><span id="infoPhone">—</span></div>
      <div class="contact-item"><span>✉️</span><span id="infoEmail">—</span></div>
      <div class="contact-item"><span>🕒</span><span id="infoHours">—</span></div>
      <a id="callBtn" href="tel:" class="call-btn">📞 Hemen Ara / Sipariş Ver</a>
    </div>
  </section>

  <!-- PANEL - LOGIN -->
  <section id="v-login" class="hidden">
    <div class="panel-wrap">
      <h2>🔐 Yönetim Paneli Girişi</h2>
      <div id="loginMsg"></div>
      <form id="loginForm">
        <label>Şifre</label>
        <input type="password" id="passInput" placeholder="Şifreyi girin (Varsayılan: 1234)" required>
        <button class="btn" type="submit" style="width:100%">Giriş Yap</button>
      </form>
    </div>
  </section>

  <!-- PANEL -->
  <section id="v-panel" class="hidden">
    <div class="panel-wrap">
      <span class="logout" onclick="logout()">Çıkış yap</span>
      <h2>⚙️ Lokanta Yönetim Paneli</h2>
      <div class="tabs">
        <button class="on" onclick="showTab('yemekler',this)">Yemekleri Yönet</button>
        <button onclick="showTab('ekle',this)">+ Yeni Yemek Ekle</button>
        <button onclick="showTab('ekipYoneticisi',this)">👨‍🍳 Şefler / Ekip</button>
        <button onclick="showTab('bilgiler',this)">Lokanta Bilgileri</button>
        <button onclick="showTab('sifre',this)">Ayarlar & Şifre</button>
      </div>
      <div id="tabMsg"></div>

      <!-- Yemek Listesi (Düzenle, Fiyat Değiştir, Sil, Durum) -->
      <div id="tab-yemekler">
        <input type="text" id="adminSearch" placeholder="🔍 Yönetilecek yemeği ara..." oninput="renderAdmin()">
        <div class="admin-list" id="adminList"></div>
      </div>

      <!-- Yeni Yemek Ekle -->
      <div id="tab-ekle" class="hidden">
        <form id="addForm">
          <label>Yemek Adı</label>
          <input id="fName" required placeholder="örn. Karnıyarık">
          
          <div class="row">
            <div>
              <label>Fiyat (₺)</label>
              <input id="fPrice" type="number" step="0.5" min="0" required placeholder="örn. 150">
            </div>
            <div>
              <label>Kategori</label>
              <select id="fCat">
                <option>Çorbalar</option>
                <option>Sulu Ev Yemekleri</option>
                <option>Pilav & Makarna</option>
                <option>Izgara & Kebaplar</option>
                <option>Salata & Mezeler</option>
                <option>Tatlılar</option>
                <option>İçecekler</option>
              </select>
            </div>
          </div>

          <label>İçerik / Açıklama</label>
          <input id="fDesc" placeholder="örn. Kıymalı, köz biber ve domates ile">

          <label>📷 Telefondan Fotoğraf Seç</label>
          <input type="file" id="fFile" accept="image/*">
          <img id="imgPreview" class="preview-box" alt="Önizleme">

          <label>veya İnternetten Fotoğraf Linki</label>
          <input id="fImg" placeholder="https://...">

          <button class="btn" type="submit" style="width:100%">Menüye Ekle</button>
        </form>
      </div>

      <!-- Şefler / Ekip Yönetimi -->
      <div id="tab-ekipYoneticisi" class="hidden">
        <form id="teamAddForm" style="margin-bottom:20px; border-bottom:1px solid #333; padding-bottom:15px;">
          <h3 style="color:var(--accent); font-size:15px; margin-bottom:10px;">Yeni Şef / Personel Ekle</h3>
          <div class="row">
            <div><label>Adı Soyadı</label><input id="tName" required placeholder="örn. Ahmet Usta"></div>
            <div><label>Unvanı / Görevi</label><input id="tRole" required placeholder="örn. Baş Aşçı"></div>
          </div>
          <button class="btn" type="submit">Ekibe Ekle</button>
        </form>
        <div class="admin-list" id="adminTeamList"></div>
      </div>

      <!-- Lokanta Bilgileri -->
      <div id="tab-bilgiler" class="hidden">
        <form id="infoForm">
          <label>Lokanta Adı</label><input id="iName" required>
          <label>Telefon Numarası</label><input id="iPhone" required>
          <label>Açık Adres</label><input id="iAddress" required>
          <label>E-posta</label><input id="iEmail" required>
          <label>Günün Menüsü / Duyuru Yazısı</label><input id="iSpecial" required>
          <div class="row">
            <div><label>Açılış Saati</label><input id="hOpen" type="time" required></div>
            <div><label>Kapanış Saati</label><input id="hClose" type="time" required></div>
          </div>
          <button class="btn" type="submit" style="width:100%">Bilgileri Kaydet</button>
        </form>
      </div>

      <!-- Şifre ve Sıfırlama -->
      <div id="tab-sifre" class="hidden">
        <form id="passForm" style="margin-bottom:24px; border-bottom:1px solid #333; padding-bottom:18px;">
          <h3 style="font-size:15px; margin-bottom:10px;">Panel Şifresini Değiştir</h3>
          <label>Mevcut Şifre</label><input id="pOld" type="password" required>
          <label>Yeni Şifre</label><input id="pNew" type="password" minlength="4" required>
          <button class="btn" type="submit">Şifreyi Güncelle</button>
        </form>
        <div>
          <h3 style="font-size:15px; margin-bottom:8px; color:var(--red);">Menüyü Sıfırla</h3>
          <p style="font-size:13px; color:var(--muted); margin-bottom:10px;">Tüm değişiklikleri silip başlangıçtaki hazır menüye döner.</p>
          <button class="btn dng" onclick="resetAll()">Fabrika Ayarlarına Dön</button>
        </div>
      </div>
    </div>
  </section>
</main>

<!-- Yemek Düzenleme Penceresi (Modal) -->
<div id="editModal" class="modal-bg hidden">
  <div class="modal">
    <h3>✏️ Yemeği Düzenle <span style="cursor:pointer;font-size:20px" onclick="closeEdit()">✕</span></h3>
    <form id="editForm">
      <input type="hidden" id="eIdx">
      <label>Yemek Adı</label>
      <input id="eName" required>
      <div class="row">
        <div>
          <label>Fiyat (₺)</label>
          <input id="ePrice" type="number" step="0.5" min="0" required>
        </div>
        <div>
          <label>Kategori</label>
          <select id="eCat">
            <option>Çorbalar</option>
            <option>Sulu Ev Yemekleri</option>
            <option>Pilav & Makarna</option>
            <option>Izgara & Kebaplar</option>
            <option>Salata & Mezeler</option>
            <option>Tatlılar</option>
            <option>İçecekler</option>
          </select>
        </div>
      </div>
      <label>Açıklama</label>
      <input id="eDesc">
      
      <label>📷 Fotoğrafı Değiştir (Telefondan Seç)</label>
      <input type="file" id="eFile" accept="image/*">
      <img id="ePreview" class="preview-box" alt="Önizleme">

      <label>veya Fotoğraf Linki</label>
      <input id="eImg">

      <div class="row" style="margin-top:8px">
        <button type="button" class="btn sec" onclick="closeEdit()">İptal</button>
        <button type="submit" class="btn">Değişiklikleri Kaydet</button>
      </div>
    </form>
  </div>
</div>

<footer>© 2026 <span id="footerName">Lezzet Lokantası</span> — Afiyet Olsun</footer>
<a class="lock-link" href="#panel" title="Yönetim Paneli">🔐</a>

<script>
const LS_ITEMS='lokanta_items_v3', LS_SET='lokanta_set_v3', LS_TEAM='lokanta_team_v3';

const DEFAULT_ITEMS=[
  {name:"Süzme Mercimek Çorbası",cat:"Çorbalar",price:65,desc:"Kızdırılmış tereyağı ve limon ile",img:"https://images.unsplash.com/photo-1547592166-23ac45744acd?w=500&q=80",on:true},
  {name:"Ezogelin Çorbası",cat:"Çorbalar",price:65,desc:"Nane ve pul biber soslu",img:"https://images.unsplash.com/photo-1604152135912-04a022e23696?w=500&q=80",on:true},
  {name:"Tavuk Suyu Çorbası",cat:"Çorbalar",price:75,desc:"Tel şehriyeli, bol tavuk parçalı",img:"https://images.unsplash.com/photo-1613844237701-8f3664fc2eff?w=500&q=80",on:true},
  {name:"Etli Kuru Fasulye",cat:"Sulu Ev Yemekleri",price:120,desc:"İspir fasulyesi, dana kuşbaşı ile",img:"https://images.unsplash.com/photo-1585032226651-759b368d7246?w=500&q=80",on:true},
  {name:"Karnıyarık",cat:"Sulu Ev Yemekleri",price:150,desc:"Kıymalı iç harç, köz biber ve domates",img:"https://images.unsplash.com/photo-1625944525533-473f1a3d54e7?w=500&q=80",on:true},
  {name:"Tas Kebabı",cat:"Sulu Ev Yemekleri",price:210,desc:"Lokum kıvamında dana eti, patates ve havuç",img:"https://images.unsplash.com/photo-1534939561126-855b8675edd7?w=500&q=80",on:true},
  {name:"Tereyağlı Pirinç Pilavı",cat:"Pilav & Makarna",price:60,desc:"Şehriyeli, tane tane",img:"https://images.unsplash.com/photo-1516684732162-798a0062be99?w=500&q=80",on:true},
  {name:"Adana Kebap",cat:"Izgara & Kebaplar",price:240,desc:"Zırh kıyması, köz domates ve biber ile",img:"https://images.unsplash.com/photo-1603360946369-dc9bb6258143?w=500&q=80",on:true},
  {name:"İskender Kebap",cat:"Izgara & Kebaplar",price:260,desc:"Yaprak döner, kızgın tereyağı ve süzme yoğurt",img:"https://images.unsplash.com/photo-1555939594-58d7cb561ad1?w=500&q=80",on:true},
  {name:"Fırın Sütlaç",cat:"Tatlılar",price:80,desc:"Üzeri nar gibi kızarmış, fındıklı",img:"https://images.unsplash.com/photo-1551024601-bec78aea704b?w=500&q=80",on:true},
  {name:"Yayık Ayran",cat:"İçecekler",price:30,desc:"Bol köpüklü, soğuk",img:"https://images.unsplash.com/photo-1541658016709-82535e94bc69?w=500&q=80",on:true}
];

const DEFAULT_TEAM=[
  {n:"Ahmet Usta",r:"Baş Aşçı"},
  {n:"Mehmet Usta",r:"Izgara & Kebap Ustası"},
  {n:"Ayşe Hanım",r:"Tatlı & Meze Sorumlusu"},
  {n:"Ali Bey",r:"Salon Şefi"}
];

function load(k,d){try{const v=localStorage.getItem(k);return v?JSON.parse(v):d}catch(e){return d}}
function save(k,v){try{localStorage.setItem(k,JSON.stringify(v))}catch(e){alert("Telefon hafızası doldu! Daha az fotoğraf ekleyin.")}}

let items=load(LS_ITEMS,DEFAULT_ITEMS);
let team=load(LS_TEAM,DEFAULT_TEAM);
let set=load(LS_SET,{
  pass:"1234",
  open:"08:00",
  close:"22:00",
  name:"Lezzet Lokantası",
  phone:"0 (352) 000 00 00",
  address:"Cumhuriyet Meydanı No:12, Merkez",
  email:"siparis@lezzetlokantasi.com",
  special:"Günün Menüsü: Mercimek Çorbası + Kuru Fasulye + Pilav + Ayran = 230 ₺"
});
let authed=sessionStorage.getItem('ld_auth')==='1';
let activeCat='Tümü';
let uploadedBase64='';
let editUploadedBase64='';

const CATS=["Çorbalar","Sulu Ev Yemekleri","Pilav & Makarna","Izgara & Kebaplar","Salata & Mezeler","Tatlılar","İçecekler"];

function esc(s){return String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function fmt(p){return Number(p).toLocaleString('tr-TR',{minimumFractionDigits:Number(p)%1?2:0})+' ₺'}

function isOpenNow(){
  const n=new Date(),c=n.getHours()*60+n.getMinutes();
  const[oh,om]=set.open.split(':').map(Number),[ch,cm]=set.close.split(':').map(Number);
  return c>=oh*60+om && c<ch*60+cm;
}

function renderInfo(){
  document.getElementById('logoText').textContent='🍽️ '+set.name;
  document.getElementById('heroTitle').textContent=set.name;
  document.getElementById('footerName').textContent=set.name;
  document.getElementById('infoAddress').textContent=set.address;
  document.getElementById('infoPhone').textContent=set.phone;
  document.getElementById('infoEmail').textContent=set.email;
  document.getElementById('infoHours').textContent=set.open+' - '+set.close;
  document.getElementById('callBtn').href='tel:'+set.phone.replace(/[^0-9+]/g,'');
  document.getElementById('specialText').textContent=set.special;
  document.title=set.name+' — Dijital Menü';
}

function renderStatus(){
  renderInfo();
  const b=document.getElementById('statusBadge');
  const open=isOpenNow();
  b.textContent=open?'● Şu An Açık':'● Şu An Kapalı';
  b.className='badge '+(open?'open':'closed');
  document.getElementById('hoursText').textContent=set.open+' - '+set.close;
}

function renderCatBar(){
  const bar=document.getElementById('catBar');
  const allCats=['Tümü',...CATS];
  bar.innerHTML=allCats.map(c=>
    `<button class="cat-pill ${activeCat===c?'active':''}" onclick="filterCat('${c}')">${c}</button>`
  ).join('');
}

function filterCat(c){
  activeCat=c;
  renderCatBar();
  renderMenu();
}

function renderMenu(){
  const area=document.getElementById('menuArea');
  const q=(document.getElementById('menuSearch')?.value||'').toLowerCase().trim();
  let h='';
  const showCats=activeCat==='Tümü'?CATS:[activeCat];
  showCats.forEach(cat=>{
    const its=items.filter(i=>i.cat===cat && (!q || i.name.toLowerCase().includes(q) || (i.desc||'').toLowerCase().includes(q)));
    if(!its.length)return;
    h+='<div class="cat-title">'+esc(cat)+'</div><div class="grid">';
    its.forEach(i=>{
      let imgTag = i.img ? '<img class="item-img" src="'+esc(i.img)+'" alt="'+esc(i.name)+'" loading="lazy">' : '';
      h+='<div class="item'+(i.on?'':' off')+'">'+imgTag+'<div class="item-content"><div><h3><span>'+esc(i.name)+(i.on?'':'<span class="tag">Tükendi</span>')+'</span><span class="price">'+fmt(i.price)+'</span></h3><p>'+esc(i.desc||'')+'</p></div></div></div>';
    });
    h+='</div>';
  });
  area.innerHTML=h || '<p style="text-align:center;color:var(--muted);padding:30px">Aradığınız yemek bulunamadı.</p>';
}

function renderTeam(){
  document.getElementById('teamArea').innerHTML=team.map(t=>
    '<div class="member"><div class="avatar">'+t.n.charAt(0).toUpperCase()+'</div><h4>'+esc(t.n)+'</h4><span>'+esc(t.r)+'</span></div>').join('');
}

function renderAdmin(){
  const q=(document.getElementById('adminSearch')?.value||'').toLowerCase().trim();
  const list=document.getElementById('adminList');
  list.innerHTML=items.map((i,x)=>{
    if(q && !i.name.toLowerCase().includes(q) && !i.cat.toLowerCase().includes(q)) return '';
    return `
      <div class="admin-card">
        <div class="admin-top">
          <img class="thumb" src="${esc(i.img||'')}" alt="">
          <div class="admin-info">
            <h4>${esc(i.name)}</h4>
            <span>${esc(i.cat)} • ${esc(i.desc||'Açıklama yok')}</span>
          </div>
        </div>
        <div class="admin-actions">
          <input type="number" step="0.5" class="price-input" value="${i.price}" onchange="updPrice(${x},this.value)" title="Fiyat"> <span>₺</span>
          <button class="btn sec sm" onclick="toggleOn(${x})">${i.on?'✓ Var':'✗ Bitti'}</button>
          <button class="btn edt sm" onclick="openEdit(${x})">✏️ Düzenle</button>
          <button class="btn dng sm" style="margin-left:auto" onclick="delItem(${x})">🗑️ Sil</button>
        </div>
      </div>`;
  }).join('');

  const tList=document.getElementById('adminTeamList');
  tList.innerHTML=team.map((t,x)=>`
    <div class="admin-card" style="flex-direction:row;align-items:center;justify-content:space-between">
      <div>
        <h4 style="font-size:15px">${esc(t.n)}</h4>
        <span style="font-size:12.5px;color:var(--muted)">${esc(t.r)}</span>
      </div>
      <button class="btn dng sm" onclick="delTeam(${x})">🗑️ Sil</button>
    </div>`).join('');
}

function msg(id,txt,ok){
  document.getElementById(id).innerHTML='<div class="msg '+(ok?'ok':'err')+'">'+txt+'</div>';
  setTimeout(()=>{const e=document.getElementById(id);if(e)e.innerHTML=''},2500);
}

// Görsel küçültme yardımcısı
function processImage(file, callback){
  const reader=new FileReader();
  reader.onload=function(ev){
    const img=new Image();
    img.onload=function(){
      const canvas=document.createElement('canvas');
      const maxW=500;
      const scale=maxW/img.width;
      canvas.width=img.width>maxW?maxW:img.width;
      canvas.height=img.width>maxW?img.height*scale:img.height;
      const ctx=canvas.getContext('2d');
      ctx.drawImage(img,0,0,canvas.width,canvas.height);
      callback(canvas.toDataURL('image/jpeg',0.75));
    };
    img.src=ev.target.result;
  };
  reader.readAsDataURL(file);
}

document.getElementById('fFile').addEventListener('change', function(e){
  if(!e.target.files[0])return;
  processImage(e.target.files[0], base64=>{
    uploadedBase64=base64;
    const prev=document.getElementById('imgPreview');
    prev.src=base64;prev.style.display='block';
  });
});

document.getElementById('eFile').addEventListener('change', function(e){
  if(!e.target.files[0])return;
  processImage(e.target.files[0], base64=>{
    editUploadedBase64=base64;
    const prev=document.getElementById('ePreview');
    prev.src=base64;prev.style.display='block';
  });
});

// Yemek Düzenleme Modalı Aç/Kapat
function openEdit(x){
  const item=items[x];
  document.getElementById('eIdx').value=x;
  document.getElementById('eName').value=item.name;
  document.getElementById('ePrice').value=item.price;
  document.getElementById('eCat').value=item.cat;
  document.getElementById('eDesc').value=item.desc||'';
  document.getElementById('eImg').value=item.img&&!item.img.startsWith('data:')?item.img:'';
  editUploadedBase64='';
  const prev=document.getElementById('ePreview');
  if(item.img){prev.src=item.img;prev.style.display='block'}else{prev.style.display='none'}
  document.getElementById('editModal').classList.remove('hidden');
}

function closeEdit(){
  document.getElementById('editModal').classList.add('hidden');
}

document.getElementById('editForm').addEventListener('submit',e=>{
  e.preventDefault();
  const x=parseInt(document.getElementById('eIdx').value);
  const linkVal=document.getElementById('eImg').value.trim();
  const finalImg = editUploadedBase64 || linkVal || items[x].img;
  items[x]={
    ...items[x],
    name:document.getElementById('eName').value.trim(),
    price:parseFloat(document.getElementById('ePrice').value)||0,
    cat:document.getElementById('eCat').value,
    desc:document.getElementById('eDesc').value.trim(),
    img:finalImg
  };
  save(LS_ITEMS,items);
  closeEdit();
  renderMenu();renderAdmin();
  msg('tabMsg','Yemek güncellendi ✓',true);
});

function route(){
  let h=(location.hash||'#anasayfa').slice(1);
  const views=['anasayfa','ekip','iletisim','login','panel'];
  if(h==='panel')h=authed?'panel':'login';
  if(!views.includes(h))h='anasayfa';
  views.forEach(v=>document.getElementById('v-'+v).classList.toggle('hidden',v!==h));
  document.querySelectorAll('[data-nav]').forEach(a=>a.classList.toggle('act',a.dataset.nav===h));
  window.scrollTo(0,0);
}

function showTab(t,btn){
  ['yemekler','ekle','ekipYoneticisi','bilgiler','sifre'].forEach(x=>document.getElementById('tab-'+x).classList.toggle('hidden',x!==t));
  document.querySelectorAll('.tabs button').forEach(b=>b.classList.remove('on'));
  if(btn)btn.classList.add('on');
  if(t==='bilgiler'){
    document.getElementById('iName').value=set.name;
    document.getElementById('iPhone').value=set.phone;
    document.getElementById('iAddress').value=set.address;
    document.getElementById('iEmail').value=set.email;
    document.getElementById('iSpecial').value=set.special;
    document.getElementById('hOpen').value=set.open;
    document.getElementById('hClose').value=set.close;
  }
}

document.getElementById('loginForm').addEventListener('submit',e=>{
  e.preventDefault();
  if(document.getElementById('passInput').value===set.pass){
    authed=true;sessionStorage.setItem('ld_auth','1');
    document.getElementById('passInput').value='';
    renderAdmin();location.hash='#panel';route();
  }else msg('loginMsg','Hatalı şifre!',false);
});

function logout(){authed=false;sessionStorage.removeItem('ld_auth');location.hash='#anasayfa';route()}

document.getElementById('addForm').addEventListener('submit',e=>{
  e.preventDefault();
  const finalImg = uploadedBase64 || document.getElementById('fImg').value.trim();
  items.unshift({
    name:document.getElementById('fName').value.trim(),
    cat:document.getElementById('fCat').value,
    price:parseFloat(document.getElementById('fPrice').value)||0,
    desc:document.getElementById('fDesc').value.trim(),
    img:finalImg,
    on:true
  });
  save(LS_ITEMS,items);
  e.target.reset();
  uploadedBase64='';
  document.getElementById('imgPreview').style.display='none';
  renderMenu();renderAdmin();msg('tabMsg','Yeni yemek eklendi ✓',true);
});

document.getElementById('teamAddForm').addEventListener('submit',e=>{
  e.preventDefault();
  team.push({
    n:document.getElementById('tName').value.trim(),
    r:document.getElementById('tRole').value.trim()
  });
  save(LS_TEAM,team);
  e.target.reset();
  renderTeam();renderAdmin();msg('tabMsg','Şef / personel eklendi ✓',true);
});

function updPrice(x,v){items[x].price=parseFloat(v)||0;save(LS_ITEMS,items);renderMenu();msg('tabMsg','Fiyat güncellendi ✓',true)}
function toggleOn(x){items[x].on=!items[x].on;save(LS_ITEMS,items);renderMenu();renderAdmin()}
function delItem(x){if(confirm('"'+items[x].name+'" menüden silinsin mi?')){items.splice(x,1);save(LS_ITEMS,items);renderMenu();renderAdmin();msg('tabMsg','Yemek silindi ✓',true)}}
function delTeam(x){if(confirm('"'+team[x].n+'" kadrodan çıkarılsın mı?')){team.splice(x,1);save(LS_TEAM,team);renderTeam();renderAdmin()}}

function resetAll(){
  if(confirm('Tüm yaptığınız değişiklikler silinecek ve varsayılan menüye dönülecek. Emin misiniz?')){
    localStorage.removeItem(LS_ITEMS);
    localStorage.removeItem(LS_TEAM);
    localStorage.removeItem(LS_SET);
    location.reload();
  }
}

document.getElementById('infoForm').addEventListener('submit',e=>{
  e.preventDefault();
  set.name=document.getElementById('iName').value.trim();
  set.phone=document.getElementById('iPhone').value.trim();
  set.address=document.getElementById('iAddress').value.trim();
  set.email=document.getElementById('iEmail').value.trim();
  set.special=document.getElementById('iSpecial').value.trim();
  set.open=document.getElementById('hOpen').value;
  set.close=document.getElementById('hClose').value;
  save(LS_SET,set);
  renderStatus();
  msg('tabMsg','Lokanta bilgileri kaydedildi ✓',true);
});

document.getElementById('passForm').addEventListener('submit',e=>{
  e.preventDefault();
  if(document.getElementById('pOld').value!==set.pass)return msg('tabMsg','Mevcut şifre hatalı!',false);
  set.pass=document.getElementById('pNew').value;save(LS_SET,set);e.target.reset();
  msg('tabMsg','Şifre değiştirildi ✓',true);
});

window.addEventListener('hashchange',route);
renderCatBar();renderMenu();renderTeam();renderStatus();route();
</script>
</body>
</html>
