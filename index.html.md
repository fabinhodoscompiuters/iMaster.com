<!doctype html>  
<html lang="pt-BR">  
<head>  
<meta charset="utf-8" />  
<meta name="viewport" content="width=device-width,initial-scale=1" />  
<title>iMaster — Simplicidade que conecta.</title>  
<meta name="description" content="iMaster — Loja conceito de iPhone e ecossistema Apple. Catálogo, carrinho e checkout simulado." />  
<style>  
  /* ----------------- Reset & base ----------------- */  
  :root{  
    --bg:#ffffff; --fg:#0b0b0c; --muted:#6b6b72; --card:#f6f6f7; --line:#e7e7ea;  
    --accent:#000000; --glass:rgba(255,255,255,0.6); --radius:14px; --shadow:0 10px 30px rgba(0,0,0,.08);  
    --maxw:1200px;  
  }  
  @media (prefers-color-scheme:dark){  
    :root{ --bg:#000; --fg:#f5f5f6; --muted:#9b9b9b; --card:#121214; --line:#232325; --glass:rgba(0,0,0,0.6); --shadow:0 10px 30px rgba(0,0,0,.6) }  
  }  
  *{box-sizing:border-box}  
  html,body{height:100%;margin:0;background:var(--bg);color:var(--fg);font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial;line-height:1.45}  
  a{color:inherit;text-decoration:none}  
  img{max-width:100%;height:auto;display:block}  
  
  /* ----------------- Layout ----------------- */  
  .wrap{max-width:var(--maxw);margin:0 auto;padding:0 20px}  
  header.nav{position:sticky;top:0;z-index:70;background:linear-gradient(to bottom,transparent,rgba(0,0,0,0.02));backdrop-filter:blur(8px);border-bottom:1px solid var(--line);padding:12px 0}  
  .nav-inner{display:flex;align-items:center;justify-content:space-between;gap:12px}  
  .brand{display:flex;align-items:center;gap:12px}  
  .brand img{height:34px; width:auto;}  
  .brand .title{font-weight:700; letter-spacing:.2px}  
  nav.menu{display:flex;gap:16px;align-items:center}  
  nav.menu a{color:var(--muted);font-weight:600;padding:8px 10px;border-radius:10px}  
  nav.menu a:hover, nav.menu a.active{color:var(--fg);background:transparent}  
  .controls{display:flex;align-items:center;gap:10px}  
  
  /* search */  
  .search{display:flex;align-items:center;gap:10px;border:1px solid var(--line);padding:8px 12px;border-radius:12px;min-width:260px;background:transparent}  
  .search input{border:0;outline:0;background:transparent;color:var(--fg);width:100%}  
  .icon-btn{border:1px solid var(--line);padding:8px 10px;border-radius:12px;background:transparent;cursor:pointer}  
  
  /* hero */  
  .hero{padding:64px 0 36px;text-align:center}  
  .hero h1{font-size:clamp(28px,6vw,54px);margin:0 0 8px}  
  .hero p{color:var(--muted);font-size:18px;margin:0 0 18px}  
  .hero .cta{display:inline-flex;gap:12px}  
  
  .btn{display:inline-block;padding:12px 18px;border-radius:999px;border:1px solid var(--line);background:var(--accent);color:#fff;font-weight:700;cursor:pointer}  
  .btn.ghost{background:transparent;color:var(--fg);border-color:var(--line)}  
  .btn.small{padding:8px 12px;font-size:14px}  
  
  /* categories */  
  .cats{display:flex;gap:10px;flex-wrap:wrap;justify-content:center;margin:26px 0}  
  .chip{padding:8px 14px;border-radius:999px;border:1px solid var(--line);color:var(--muted);cursor:pointer}  
  .chip.active{border-color:var(--fg);color:var(--fg)}  
  
  /* grid */  
  .grid{display:grid;grid-template-columns:repeat(12,1fr);gap:20px}  
  .card{grid-column:span 4;background:var(--card);border-radius:12px;padding:14px;border:1px solid var(--line);box-shadow:var(--shadow);display:flex;flex-direction:column;gap:10px;transition:transform .18s}  
  .card:hover{transform:translateY(-6px)}  
  .card img{border-radius:10px;object-fit:contain;height:220px;width:100%;background:linear-gradient(180deg,#fff0,#fff0)}  
  .kicker{font-size:12px;color:var(--muted);text-transform:uppercase;letter-spacing:.6px}  
  .title{font-size:18px;font-weight:700}  
  .desc{color:var(--muted);font-size:14px}  
  .price{font-weight:800;font-size:18px;margin-top:6px}  
  
  .actions{display:flex;gap:8px;align-items:center;margin-top:auto}  
  .actions .qty{display:flex;gap:8px;align-items:center;border:1px solid var(--line);padding:6px 10px;border-radius:10px}  
  .actions button{background:transparent;border:0;cursor:pointer;font-size:16px}  
  
  /* cart drawer */  
  .drawer{position:fixed;top:0;right:-420px;bottom:0;width:400px;background:var(--bg);border-left:1px solid var(--line);box-shadow:var(--shadow);transition:right .28s;z-index:120;display:flex;flex-direction:column}  
  .drawer.open{right:0}  
  .drawer header{padding:16px;border-bottom:1px solid var(--line);display:flex;justify-content:space-between;align-items:center}  
  .cart-list{padding:12px;overflow:auto;flex:1;display:flex;flex-direction:column;gap:12px}  
  .cart-item{display:flex;gap:12px;align-items:center;border:1px solid var(--line);padding:10px;border-radius:10px}  
  .cart-item img{width:64px;height:64px;object-fit:cover;border-radius:8px}  
  .cart-footer{padding:14px;border-top:1px solid var(--line)}  
  .total{display:flex;justify-content:space-between;font-weight:800;margin-bottom:8px}  
  
  /* support */  
  section.support{padding:40px 0}  
  .faq{max-width:900px;margin:0 auto;display:grid;gap:12px}  
  details{background:var(--card);border:1px solid var(--line);padding:12px;border-radius:10px}  
  summary{cursor:pointer;font-weight:700}  
  
  /* footer */  
  footer{padding:36px 0;border-top:1px solid var(--line);color:var(--muted);font-size:14px;text-align:center;margin-top:40px}  
  
  /* responsive */  
  @media (max-width:980px){  
    .card{grid-column:span 6}  
    .search{display:none}  
  }  
  @media (max-width:640px){  
    .card{grid-column:span 12}  
    nav.menu{display:none}  
    .nav-inner{justify-content:space-between}  
  }  
</style>  
</head>  
<body>  
  
<!-- NAV -->  
<header class="nav">  
  <div class="wrap nav-inner">  
    <div class="brand">  
      <!-- if you have a local logo file named logo.png, it will show; otherwise text -->  
      <img src="logo.png" alt="iMaster logo" onerror="this.style.display='none'">  
      <div class="title">iMaster</div>  
    </div>  
  
    <nav class="menu" aria-label="Main">  
      <a href="#catalogo" class="active">Loja</a>  
      <a href="#eco">Ecossistema</a>  
      <a href="#suporte">Suporte</a>  
      <a href="#contato">Contato</a>  
    </nav>  
  
    <div class="controls">  
      <div class="search" role="search" aria-label="Buscar produtos">  
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none"><path d="M21 21l-4.3-4.3m1.8-5.2a7 7 0 11-14 0 7 7 0 0114 0z" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round"/></svg>  
        <input id="globalSearch" placeholder="Buscar: iPhone, capa, carregador..." />  
      </div>  
      <button class="icon-btn" id="cartBtn" title="Abrir sacola">🛍️</button>  
    </div>  
  </div>  
</header>  
  
<!-- HERO -->  
<section class="hero wrap">  
  <h1>Simplicidade que conecta.</h1>  
  <p>iMaster — curadoria premium de iPhone, acessórios e o ecossistema Apple. Compra simulada para apresentação escolar.</p>  
  <div class="cta">  
    <a class="btn" href="#catalogo">Explorar produtos</a>  
    <a class="btn ghost" href="#suporte">Dicas & Suporte</a>  
  </div>  
</section>  
  
<!-- CATALOG -->  
<section id="catalogo" class="wrap">  
  <div style="display:flex;justify-content:space-between;align-items:end;gap:12px">  
    <div>  
      <div class="kicker">Catálogo</div>  
      <h2 style="margin:6px 0 0">Em destaque</h2>  
    </div>  
    <div style="text-align:right">  
      <div class="kicker" style="margin-bottom:6px">Loja • iMaster</div>  
      <div style="display:flex;gap:8px;justify-content:flex-end">  
        <div class="chip active" data-cat="all">Tudo</div>  
        <div class="chip" data-cat="iphone">iPhone</div>  
        <div class="chip" data-cat="ipad">iPad</div>  
        <div class="chip" data-cat="mac">Mac</div>  
        <div class="chip" data-cat="watch">Watch</div>  
        <div class="chip" data-cat="acessorios">Acessórios</div>  
      </div>  
    </div>  
  </div>  
  
  <div class="grid" id="grid" style="margin-top:20px"></div>  
</section>  
  
<!-- ECOSSISTEMA -->  
<section id="eco" class="wrap" style="padding-top:36px">  
  <div style="display:flex;gap:20px;align-items:center;flex-wrap:wrap">  
    <div style="flex:1;min-width:240px">  
      <h3>Ecossistema Apple</h3>  
      <p style="color:var(--muted)">iPhone, iPad, Mac, Watch e acessórios que conversam entre si. Conectividade, segurança e experiência integrada.</p>  
      <ul style="color:var(--muted)">  
        <li>Integração iCloud & Handoff</li>  
        <li>Segurança: Buscar, 2FA e Chave-sinal</li>  
        <li>Periféricos oficiais e certificados</li>  
      </ul>  
    </div>  
    <div style="flex:1;min-width:240px">  
      <img src="https://www.apple.com/v/home/ae/images/heroes/home_hero_mac__e9d2y4w3syi2_large.jpg" alt="Ecosistema" style="border-radius:12px;box-shadow:var(--shadow)">  
    </div>  
  </div>  
</section>  
  
<!-- SUPORTE -->  
<section id="suporte" class="support wrap" style="padding-top:36px">  
  <div class="kicker">Ajuda</div>  
  <h2 style="margin:6px 0 12px">Suporte iMaster</h2>  
  <div class="faq">  
    <details open><summary>Como faço backup antes de trocar de iPhone?</summary><div style="color:var(--muted);margin-top:8px">Ative Backup no iCloud em Ajustes › [seu nome] › iCloud › Backup. Para transferir, use "Início Rápido" aproximando os aparelhos.</div></details>  
    <details><summary>Como preservar a bateria?</summary><div style="color:var(--muted);margin-top:8px">Ative Carregamento Otimizado, evite calor extremo e prefira carregadores certificados.</div></details>  
    <details><summary>O que checar ao comprar um seminovo?</summary><div style="color:var(--muted);margin-top:8px">Verifique IMEI/IMEI block, capacidade de bateria e histórico de manutenção; peça nota fiscal sempre que possível.</div></details>  
    <details><summary>Política de garantia</summary><div style="color:var(--muted);margin-top:8px">Garantia de 90 dias para defeitos em aparelhos seminovos; acessórios têm garantia conforme fabricante.</div></details>  
  </div>  
  <p style="color:var(--muted);margin-top:12px">Este é um protótipo para apresentação. Informações meramente ilustrativas.</p>  
</section>  
  
<!-- CONTATO / LOJA -->  
<section id="contato" class="wrap" style="padding-top:36px;padding-bottom:36px">  
  <div style="display:grid;grid-template-columns:1fr 360px;gap:20px">  
    <div style="background:var(--card);padding:20px;border-radius:12px;border:1px solid var(--line)">  
      <h3>Visite a iMaster</h3>  
      <p style="color:var(--muted)">Rua Juvelina Ferreira de Assis, 50 — Vila Carrão, São Paulo • CEP 03449-060</p>  
      <p style="color:var(--muted)">Horário: Seg–Sáb, 10h–19h</p>  
      <p style="color:var(--muted)">WhatsApp: <a href="https://wa.me/5511969485635" target="_blank">(11) 96948-5635</a></p>  
      <div style="margin-top:12px">  
        <a class="btn whatsapp" href="https://wa.me/5511969485635" target="_blank" style="background:#25D366">Falar no WhatsApp</a>  
        <a class="btn ghost" href="#" onclick="alert('Formulário simulado');return false;">Enviar mensagem</a>  
      </div>  
    </div>  
  
    <div style="background:var(--card);padding:20px;border-radius:12px;border:1px solid var(--line)">  
      <h4>Transparência</h4>  
      <p style="color:var(--muted)">CNPJ: 45.678.123/0001-90 • iMaster Comércio de Celulares Ltda</p>  
      <p style="color:var(--muted)">Política de trocas e garantias ilustrativa para fins acadêmicos.</p>  
    </div>  
  </div>  
</section>  
  
<!-- CART DRAWER -->  
<aside class="drawer" id="cartDrawer" aria-hidden="true">  
  <header>  
    <strong>Sua sacola</strong>  
    <div>  
      <button class="icon-btn" id="closeCart">Fechar</button>  
    </div>  
  </header>  
  <div class="cart-list" id="cartList">  
    <div style="color:var(--muted);padding:12px">Nenhum item na sacola.</div>  
  </div>  
  <div class="cart-footer">  
    <div class="total"><span>Subtotal</span><span id="subtotal">R$ 0,00</span></div>  
    <div style="display:flex;gap:8px">  
      <button class="btn" id="checkoutBtn">Finalizar compra</button>  
      <button class="btn ghost" id="clearBtn">Limpar</button>  
    </div>  
    <div style="margin-top:8px;color:var(--muted);font-size:13px">Checkout simulado — sem transações reais (projeto escolar).</div>  
  </div>  
</aside>  
  
<footer>  
  <div class="wrap">  
    <div style="display:flex;justify-content:space-between;gap:12px;align-items:center;flex-wrap:wrap">  
      <div style="min-width:160px">  
        <strong>iMaster</strong><div style="color:var(--muted);font-size:13px">Simplicidade que conecta.</div>  
      </div>  
      <div style="color:var(--muted);font-size:13px">© <span id="year"></span> iMaster — Protótipo para trabalho escolar. Não afiliado à Apple Inc.</div>  
    </div>  
  </div>  
</footer>  
  
<script>  
/* ================= Data: catálogo ================= */  
const catalog = [  
  {id:'ip15pro',cat:'iphone',name:'iPhone 15 Pro',desc:'Titanium • A17 Pro • 128–1TB',price:8999,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/iphone-15-pro-finish-select-202309-6-1inch-titanium?wid=512&hei=512&fmt=png-alpha'},  
  {id:'ip15',cat:'iphone',name:'iPhone 15',desc:'Ilha Dinâmica • 48 MP',price:6799,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/iphone-15-finish-select-202309-6-1inch-blue?wid=512&hei=512&fmt=png-alpha'},  
  {id:'ipse',cat:'iphone',name:'iPhone SE',desc:'A15 Bionic • Touch ID',price:2999,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/iphone-se-finish-unselect-gallery-1-202207?wid=512&hei=512&fmt=png-alpha'},  
  {id:'ipad10',cat:'ipad',name:'iPad 10ª geração',desc:'10,9” • A14',price:3599,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/ipad-10th-gen-finish-blue-wifi-select?wid=512&hei=512&fmt=png-alpha'},  
  {id:'ipadpro',cat:'ipad',name:'iPad Pro',desc:'M2 • ProMotion',price:8999,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/ipad-pro-11-select-cell-silver-202210?wid=512&hei=512&fmt=png-alpha'},  
  {id:'macair',cat:'mac',name:'MacBook Air M2',desc:'M2 • Leve e potente',price:7999,img:'https://www.apple.com/v/mac/home/bi/images/overview/compare_mac_m2__e9cudk8b4vqe_large.jpg'},  
  {id:'watch9',cat:'watch',name:'Apple Watch Series 9',desc:'GPS • 41/45 mm',price:3499,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MREY3?wid=512&hei=512&fmt=png-alpha'},  
  {id:'airpodspro2',cat:'acessorios',name:'AirPods Pro (2ª gen)',desc:'ANC e Áudio Espacial',price:2299,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/airpods-pro-charging-case-usb-c-202309?wid=512&hei=512&fmt=png-alpha'},  
  {id:'capinha',cat:'acessorios',name:'Capinha MagSafe',desc:'Transparente • Proteção',price:249,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/MPU63?wid=512&hei=512&fmt=png-alpha'},  
  {id:'carreg',cat:'acessorios',name:'Carregador 20W',desc:'USB-C rápido',price:219,img:'https://store.storeimages.cdn-apple.com/4982/as-images.apple.com/is/mhje3?wid=512&hei=512&fmt=png-alpha'}  
];  
  
/* =============== Utilidades =============== */  
const $ = sel => document.querySelector(sel);  
const $$ = sel => Array.from(document.querySelectorAll(sel));  
const money = v => v.toLocaleString('pt-BR',{style:'currency',currency:'BRL'});  
  
/* =============== Render catálogo =============== */  
const grid = $('#grid');  
let catFilter = 'all';  
let q = '';  
  
function render(){  
  grid.innerHTML = '';  
  const list = catalog.filter(p=>{  
    const okCat = catFilter==='all' || p.cat===catFilter;  
    const okQ = !q || (p.name+' '+p.desc).toLowerCase().includes(q);  
    return okCat && okQ;  
  });  
  list.forEach(p=>{  
    const el = document.createElement('article');  
    el.className='card';  
    el.innerHTML = `  
      <img src="${p.img}" alt="${p.name}">  
      <div class="kicker">${p.cat.toUpperCase()}</div>  
      <div class="title">${p.name}</div>  
      <div class="desc">${p.desc}</div>  
      <div class="price">${money(p.price)}</div>  
      <div class="actions">  
        <div class="qty">  
          <button onclick="chgQty('${p.id}',-1)">−</button>  
          <span id="q_${p.id}">1</span>  
          <button onclick="chgQty('${p.id}',1)">+</button>  
        </div>  
        <button class="btn ghost" onclick="addToCart('${p.id}')">Adicionar</button>  
      </div>  
    `;  
    grid.appendChild(el);  
  });  
}  
render();  
  
/* =============== filtros e busca =============== */  
$$('.chip').forEach(ch=>{  
  ch.addEventListener('click', ()=>{  
    $$('.chip').forEach(x=>x.classList.remove('active'));  
    ch.classList.add('active');  
    catFilter = ch.dataset.cat;  
    render();  
  });  
});  
$('#globalSearch').addEventListener('input', e=>{  
  q = e.target.value.trim().toLowerCase();  
  render();  
});  
  
/* =============== carrinho =============== */  
const cart = {}; // id -> qty  
function chgQty(id,delta){  
  const el = document.getElementById('q_'+id);  
  let v = parseInt(el.textContent||'0') + delta;  
  if(v < 1) v = 1;  
  el.textContent = v;  
}  
function addToCart(id){  
  const qEl = document.getElementById('q_'+id);  
  const qty = parseInt(qEl.textContent||'1',10) || 1;  
  cart[id] = (cart[id]||0) + qty;  
  qEl.textContent = '1';  
  openCart();  
  updateCart();  
}  
  
/* Drawer behavior */  
const cartDrawer = document.getElementById('cartDrawer');  
$('#cartBtn').addEventListener('click', openCart);  
$('#closeCart').addEventListener('click', ()=>cartDrawer.classList.remove('open'));  
function openCart(){ cartDrawer.classList.add('open'); updateCart(); }  
  
/* Render cart */  
function updateCart(){  
  const list = $('#cartList');  
  list.innerHTML = '';  
  const keys = Object.keys(cart);  
  if(keys.length===0){  
    list.innerHTML = '<div style="padding:12px;color:var(--muted)">Nenhum item na sacola.</div>';  
    $('#subtotal').textContent = money(0);  
    return;  
  }  
  let total = 0;  
  keys.forEach(id=>{  
    const p = catalog.find(x=>x.id===id);  
    if(!p) return;  
    const qty = cart[id];  
    total += p.price * qty;  
    const node = document.createElement('div');  
    node.className = 'cart-item';  
    node.innerHTML = `  
      <img src="${p.img}" alt="${p.name}">  
      <div style="flex:1">  
        <div style="font-weight:700">${p.name}</div>  
        <div style="color:var(--muted);font-size:13px;margin-top:6px">${qty} × ${money(p.price)}</div>  
      </div>  
      <div style="display:flex;flex-direction:column;gap:8px;">  
        <button class="icon-btn" onclick="removeItem('${id}')">Remover</button>  
      </div>  
    `;  
    list.appendChild(node);  
  });  
  $('#subtotal').textContent = money(total);  
}  
function removeItem(id){ delete cart[id]; updateCart(); }  
  
$('#clearBtn').addEventListener('click', ()=>{  
  if(confirm('Limpar a sacola?')){ for(const k in cart) delete cart[k]; updateCart(); }  
});  
  
/* Checkout simulado */  
$('#checkoutBtn').addEventListener('click', ()=>{  
  const keys = Object.keys(cart);  
  if(keys.length===0){ alert('Sua sacola está vazia.'); return; }  
  // coletar dados simples (simulado)  
  const nome = prompt('Nome para o pedido (simulado):');  
  if(!nome){ alert('Pedido cancelado'); return; }  
  alert(`Pedido SIMULADO confirmado ✅\n\nNome: ${nome}\nItens: ${keys.length}\n\n(Projeto escolar — sem pagamento real)`);  
  // limpar  
  for(const k in cart) delete cart[k];  
  updateCart();  
  cartDrawer.classList.remove('open');  
});  
  
/* inicial */  
document.getElementById('year').textContent = new Date().getFullYear();  
</script>  
</body>  
</html>  
