# ryadom-new
Рядом — услуги твоего города

<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Рядом — твой город, твои возможности</title>

<style>
:root{
--blue:#4263eb;
--blue2:#2849cf;
--bg:#f5f7fb;
--white:#fff;
--text:#172033;
--muted:#8791a5;
--border:#e9edf5;
--green:#19b982;
}
*{box-sizing:border-box}
body{
margin:0;background:var(--bg);color:var(--text);
font:15px Arial,sans-serif;
}
button,input,textarea,select{font:inherit}
button{cursor:pointer}
button:hover{opacity:.85}
a{text-decoration:none;color:inherit}

.app{display:grid;grid-template-columns:250px 1fr;min-height:100vh}
.sidebar{
background:white;border-right:1px solid var(--border);
padding:25px 18px;position:sticky;top:0;height:100vh;
display:flex;flex-direction:column;gap:30px
}
.logo{font-size:27px;font-weight:900;display:flex;align-items:center;gap:10px}
.logo-icon{
width:43px;height:43px;border-radius:15px;
background:linear-gradient(135deg,#7294ff,#3457e7);
color:white;display:grid;place-items:center;font-size:25px
}
.menu{display:grid;gap:6px}
.menu button{
border:0;background:transparent;padding:15px;border-radius:13px;
text-align:left;color:#68748a;display:flex;gap:13px;align-items:center;
font-weight:700
}
.menu button span{font-size:22px;width:25px}
.menu button.active,.menu button:hover{background:#edf1ff;color:var(--blue)}
.sidebar-bottom{
margin-top:auto;background:#f0f3ff;padding:20px;border-radius:18px
}
.sidebar-bottom button{width:100%;padding:12px;background:#4263eb;color:white;border:0;border-radius:12px;font-weight:bold}

main{padding:25px;min-width:0}
.topbar{display:flex;align-items:center;gap:12px;margin-bottom:25px}
.search{
flex:1;background:white;border:1px solid var(--border);
border-radius:15px;padding:0 15px;display:flex;align-items:center
}
.search input{border:0;outline:0;width:100%;padding:15px;background:transparent}
.btn{border:0;border-radius:13px;padding:14px 18px;font-weight:800}
.primary{background:var(--blue);color:white}
.secondary{background:white;border:1px solid var(--border)}
.avatar{width:43px;height:43px;border-radius:50%;object-fit:cover;cursor:pointer}

.hero{
background:linear-gradient(115deg,#2546c8,#527bff);
border-radius:25px;padding:40px;color:white;position:relative;
overflow:hidden;min-height:300px;display:flex;align-items:center
}
.hero:after{
content:"✦";position:absolute;right:8%;top:-80px;
font-size:350px;color:#ffffff12
}
.hero-content{position:relative;z-index:1;max-width:650px}
.hero h1{font-size:clamp(35px,5vw,58px);margin:0 0 17px;line-height:1.05}
.hero p{font-size:18px;line-height:1.6;color:#e3eaff;max-width:480px}
.hero-search{
display:flex;background:white;padding:5px;border-radius:14px;
max-width:550px;margin-top:25px
}
.hero-search input{flex:1;min-width:0;border:0;outline:0;padding:14px;color:#172033}
.hero-search button{border:0;border-radius:11px;background:#172033;color:white;padding:0 22px;font-weight:bold}

.stats{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin:18px 0}
.stat{background:white;border:1px solid var(--border);border-radius:17px;padding:18px}
.stat strong{font-size:23px;display:block;margin-bottom:6px}
.stat small{color:var(--muted)}

.section{background:white;border:1px solid var(--border);border-radius:21px;padding:22px;margin-bottom:18px}
.section-head{display:flex;align-items:center;justify-content:space-between;gap:10px;margin-bottom:18px}
h2{font-size:23px;margin:0}
.link{border:0;background:transparent;color:var(--blue);font-weight:bold}

.categories{display:grid;grid-template-columns:repeat(5,1fr);gap:10px}
.category{
background:#f6f8ff;border:1px solid #edf0ff;border-radius:16px;
padding:17px 5px;text-align:center
}
.category:hover,.category.selected{background:#e5edff;border-color:#b8ccff}
.category span{font-size:30px;display:block;margin-bottom:10px}
.category b{font-size:12px}

.filters{display:flex;gap:9px;flex-wrap:wrap;margin-bottom:18px}
.filter{border:1px solid var(--border);background:white;border-radius:30px;padding:9px 17px;color:#66748b}
.filter.active{background:var(--blue);color:white;border-color:var(--blue)}

.cards{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:15px}
.card{
background:white;border:1px solid var(--border);border-radius:18px;
overflow:hidden;transition:.2s
}
.card:hover{transform:translateY(-4px);box-shadow:0 12px 35px #263b7015}
.card-img{width:100%;height:170px;object-fit:cover;background:#edf1ff}
.card-body{padding:15px}
.rating{font-size:12px;color:#7c879b;margin-bottom:10px}
.rating b{color:#f5ad21}
.card h3{font-size:16px;margin:0 0 10px;min-height:38px;line-height:1.4}
.price{font-weight:900;font-size:18px}
.location{color:var(--muted);font-size:12px;margin-top:9px}
.card-bottom{display:flex;align-items:center;justify-content:space-between;margin-top:14px}
.heart{border:0;background:#f1f4ff;border-radius:11px;padding:9px 13px;color:#75839b;font-size:19px}
.heart.liked{color:#ff4168}
.arrow{border:0;background:var(--blue);color:white;border-radius:11px;width:36px;height:36px;font-size:20px}

.rightbox{background:white;border:1px solid var(--border);border-radius:19px;padding:20px;margin-bottom:15px}
.rightbox h3{margin:0 0 15px}
.promo{background:linear-gradient(135deg,#7948e9,#a27cff);color:white;border-radius:20px;padding:22px}
.promo button{background:white;color:#6845d2;border:0;border-radius:12px;padding:12px;font-weight:bold}
.promo p{color:#eee4ff;line-height:1.5}
.layout{display:grid;grid-template-columns:minmax(0,1fr) 255px;gap:18px}
.city{display:block;width:100%;text-align:left;border:0;background:transparent;padding:10px;color:#66748b}
.city:hover{color:var(--blue);background:#f4f6ff;border-radius:10px}

.page{display:none}
.page.active{display:block}
.page-title{font-size:32px;margin:8px 0 22px}
.empty{padding:35px;text-align:center;color:var(--muted)}
.profile{
display:flex;gap:20px;align-items:center;background:#f3f6ff;
padding:22px;border-radius:18px;margin-bottom:20px
}
.profile img{width:95px;height:95px;border-radius:50%;object-fit:cover}
.form{display:grid;gap:14px}
.form label{display:grid;gap:7px;font-weight:bold}
.form input,.form textarea,.form select{
width:100%;padding:14px;border:1px solid var(--border);
border-radius:12px;background:white;outline-color:#9ab5ff
}
.form textarea{min-height:110px}
.order{border:1px solid var(--border);padding:18px;border-radius:15px;margin-bottom:12px}
.order h3{margin-top:0}
.mobile-nav{display:none}
.toast{
position:fixed;bottom:25px;left:50%;transform:translateX(-50%);
background:#172033;color:white;padding:15px 22px;border-radius:13px;
display:none;z-index:200
}
.modal-bg{
display:none;position:fixed;inset:0;background:#10172b99;
z-index:100;align-items:center;justify-content:center;padding:15px
}
.modal-bg.show{display:flex}
.modal{background:white;border-radius:22px;padding:25px;width:min(480px,100%)}
.modal-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:20px}
.close{border:0;background:#edf1fa;border-radius:10px;width:35px;height:35px;font-size:22px}

@media(max-width:1150px){
.layout{grid-template-columns:1fr}
.right{display:grid;grid-template-columns:repeat(2,1fr)}
.cards{grid-template-columns:repeat(2,minmax(0,1fr))}
}
@media(max-width:700px){
.app{grid-template-columns:1fr}
.sidebar{display:none}
main{padding:12px 10px 90px}
.layout{grid-template-columns:1fr}
.right{display:none}
.hero{padding:25px;min-height:290px}
.hero h1{font-size:38px}
.stats{grid-template-columns:repeat(2,1fr)}
.categories{grid-template-columns:repeat(4,1fr)}
.cards{grid-template-columns:repeat(2,minmax(0,1fr));gap:9px}
.card-img{height:125px}
.card-body{padding:10px}
.card h3{font-size:13px}
.price{font-size:15px}
.mobile-nav{
display:flex;position:fixed;bottom:0;left:0;right:0;
background:#ffffffed;backdrop-filter:blur(12px);
border-top:1px solid var(--border);justify-content:space-around;
padding:10px 4px calc(10px + env(safe-area-inset-bottom));z-index:30
}
.mobile-nav button{border:0;background:transparent;color:#66748b;font-size:10px;display:grid;justify-items:center;gap:4px}
.mobile-nav span{font-size:21px}
.section{padding:14px}
}
 
/* Анимация появления */
@keyframes rise {
  from { opacity:0; transform:translateY(35px); }
  to { opacity:1; transform:translateY(0); }
}

/* Светящийся фон */
body {
  background:
    radial-gradient(ellipse at 20% 10%, #38208033, transparent 40%),
    radial-gradient(ellipse at 80% 50%, #124a8830, transparent 45%),
    #070914;
  background-attachment:fixed;
}

/* Плавное появление блоков */
section {
  animation:rise .8s ease both;
}

/* Неоновое свечение */
.btn {
  box-shadow:0 0 20px #7257ff44;
  transition:.3s;
}
.btn:hover {
  transform:translateY(-3px);
  box-shadow:0 0 30px #7257ff88;
}

/* Красивые карточки */
.service {
  position:relative;
  transition:transform .35s, border-color .35s;
}
.service:hover {
  transform:translateY(-8px) scale(1.015);
  border-color:#806aff;
  box-shadow:0 10px 40px #7257ff22;
}

/* Категории */
.category {
  transition:.3s;
}
.category:hover {
  box-shadow:0 0 25px #7257ff33;
}

/* Мягкие градиенты */
.hero {
  background:
    linear-gradient(180deg,#07091420,#070914ee),
    url("city-map.png") center/cover;
}

/* Красивые изображения */
.servicepic img {
  width:100%;
  height:100%;
  object-fit:cover;
  transition:transform .5s;
}
.service:hover .servicepic img {
  transform:scale(1.08);
}
 
</style>
</head>

<body>
<div class="app">

<aside class="sidebar">
<div class="logo"><div class="logo-icon">⌖</div>Рядом</div>
<nav class="menu">
<button class="active" onclick="go('home')"><span>⌂</span> Главная</button>
<button onclick="go('catalog')"><span>▦</span> Каталог</button>
<button onclick="go('masters')"><span>♙</span> Исполнители</button>
<button onclick="go('orders')"><span>▤</span> Объявления</button>
<button onclick="go('favorites')"><span>♡</span> Избранное</button>
<button onclick="go('profile')"><span>♟</span> Профиль</button>
</nav>
<div class="sidebar-bottom">
<div style="font-size:28px">✨</div>
<b>Рядом Premium</b>
<p style="font-size:13px;color:#7c879b">Больше возможностей для тебя</p>
<button onclick="toast('Скоро появится!')">Подробнее</button>
</div>
</aside>

<main>
<header class="topbar">
<div class="search">⌕ <input id="search" placeholder="Найти услугу..." oninput="render()"></div>
<button class="btn secondary" onclick="go('favorites')">♡</button>
<button class="btn primary" onclick="openOrder()">＋ Заказ</button>
<img class="avatar" onclick="go('profile')" src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=100">
</header>

<div class="layout">
<div>

<section id="home" class="page active">
<div class="hero">
<div class="hero-content">
<h1>Всё нужное.<br>Совсем рядом.</h1>
<p>Находи мастеров, заказывай услуги и открывай новые возможности своего города.</p>
<div class="hero-search">
<input id="heroSearch" placeholder="Что тебе нужно?" onkeydown="if(event.key==='Enter')searchHero()">
<button onclick="searchHero()">Найти →</button>
</div>
</div>
</div>

<div class="stats">
<div class="stat"><strong>⚡ Быстро</strong><small>Удобный поиск</small></div>
<div class="stat"><strong>🛡️ Надёжно</strong><small>Профили мастеров</small></div>
<div class="stat"><strong>💎 Удобно</strong><small>Всё в одном месте</small></div>
<div class="stat"><strong>💙 Рядом</strong><small>Твой город</small></div>
</div>

<div class="section">
<div class="section-head"><h2>Категории</h2><button class="link" onclick="go('catalog')">Все →</button></div>
<div class="categories" id="categories"></div>
</div>

<div class="section">
<div class="section-head"><h2>🔥 Популярное</h2><button class="link" onclick="go('catalog')">Каталог →</button></div>
<div class="cards" id="homeCards"></div>
</div>
</section>

<section id="catalog" class="page">
<h1 class="page-title">Каталог услуг</h1>
<div class="section">
<div class="section-head"><h2>Выбери категорию</h2></div>
<div class="categories" id="catalogCategories"></div>
</div>
<div class="section">
<div class="section-head"><h2 id="catalogTitle">Все предложения</h2></div>
<div class="filters" id="filters"></div>
<div class="cards" id="catalogCards"></div>
</div>
</section>

<section id="masters" class="page">
<h1 class="page-title">Исполнители</h1>
<div class="section">
<p style="color:#8791a5">Знакомься с мастерами своего города.</p>
<div class="cards" id="masterCards"></div>
</div>
</section>

<section id="orders" class="page">
<h1 class="page-title">Объявления</h1>
<div class="section">
<div class="section-head"><h2>Заказы пользователей</h2><button class="btn primary" onclick="openOrder()">＋ Создать</button></div>
<div id="orderList"></div>
</div>
</section>

<section id="favorites" class="page">
<h1 class="page-title">Избранное</h1>
<div class="section"><div class="cards" id="favoriteCards"></div></div>
</section>

<section id="profile" class="page">
<h1 class="page-title">Мой профиль</h1>
<div class="section">
<div class="profile">
<img src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=300">
<div><h2 id="profileTitle">Валера</h2><p style="color:#8791a5">Участник Рядом</p>⭐ Новый пользователь</div>
</div>
<form class="form" onsubmit="saveProfile(event)">
<label>Имя<input id="profileName" value="Валера"></label>
<label>Город<input id="profileCity" value="Минеральные Воды"></label>
<label>О себе<textarea id="profileAbout" placeholder="Расскажи о себе"></textarea></label>
<button class="btn primary">Сохранить профиль</button>
</form>
</div>
</section>

</div>

<aside class="right">
<div class="promo">
<div style="font-size:30px">👑</div>
<h2>Рядом Premium</h2>
<p>Больше возможностей для твоего профиля и объявлений.</p>
<button onclick="toast('Premium скоро появится!')">Узнать больше →</button>
</div>
<div class="rightbox">
<h3>📍 Популярные города</h3>
<button class="city" onclick="setCity('Минеральные Воды')">Минеральные Воды</button>
<button class="city" onclick="setCity('Москва')">Москва</button>
<button class="city" onclick="setCity('Санкт-Петербург')">Санкт-Петербург</button>
<button class="city" onclick="setCity('Екатеринбург')">Екатеринбург</button>
<button class="city" onclick="setCity('Казань')">Казань</button>
</div>
<div class="rightbox">
<h3>💡 Возможности</h3>
<p>🔎 Поиск услуг</p><p>❤️ Избранное</p><p>📄 Объявления</p><p>👤 Профили</p>
</div>
</aside>
</div>
</main>
</div>

<nav class="mobile-nav">
<button onclick="go('home')"><span>⌂</span>Главная</button>
<button onclick="go('catalog')"><span>▦</span>Каталог</button>
<button onclick="openOrder()"><span>＋</span>Заказ</button>
<button onclick="go('favorites')"><span>♡</span>Избранное</button>
<button onclick="go('profile')"><span>♟</span>Профиль</button>
</nav>

<div class="modal-bg" id="orderModal">
<div class="modal">
<div class="modal-head"><h2>Создать объявление</h2><button class="close" onclick="closeOrder()">×</button></div>
<form class="form" onsubmit="publishOrder(event)">
<input id="newTitle" required placeholder="Что нужно сделать?">
<select id="newCategory"><option>Ремонт</option><option>Уборка</option><option>Доставка</option><option>Красота</option><option>IT</option><option>Обучение</option><option>Питомцы</option><option>Другое</option></select>
<input id="newCity" required value="Минеральные Воды" placeholder="Город">
<textarea id="newDescription" placeholder="Подробности заказа"></textarea>
<button class="btn primary">Опубликовать</button>
</form>
</div>
</div>

<div class="toast" id="toast"></div>

<script>
const categories=[
["🔧","Ремонт"],["🧹","Уборка"],["🚚","Доставка"],
["💄","Красота"],["💻","IT"],["🎓","Обучение"],
["🐾","Питомцы"],["📷","Фото"],["🚘","Авто"],["🎨","Другое"]
];

const services=[
{id:1,name:"Ремонт компьютеров",cat:"IT",price:"от 500 ₽",city:"Минеральные Воды",rating:"4.9",img:"https://images.unsplash.com/photo-1588872657578-7efd1f1555ed?w=600",desc:"Диагностика и ремонт компьютеров и ноутбуков."},
{id:2,name:"Генеральная уборка",cat:"Уборка",price:"от 2 000 ₽",city:"Минеральные Воды",rating:"4.8",img:"https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=600",desc:"Уборка квартиры и помещений."},
{id:3,name:"Профессиональный макияж",cat:"Красота",price:"от 2 500 ₽",city:"Москва",rating:"5.0",img:"https://images.unsplash.com/photo-1522335789203-aabd1fc54bc9?w=600",desc:"Дневной и вечерний макияж."},
{id:4,name:"Аренда автомобиля",cat:"Авто",price:"от 3 000 ₽",city:"Москва",rating:"4.9",img:"https://images.unsplash.com/photo-1503376780353-7e6692767b70?w=600",desc:"Автомобили на сутки и длительный срок."},
{id:5,name:"Муж на час",cat:"Ремонт",price:"от 1 000 ₽",city:"Минеральные Воды",rating:"4.8",img:"https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=600",desc:"Мелкий ремонт, сборка мебели и установка."},
{id:6,name:"Доставка документов",cat:"Доставка",price:"от 400 ₽",city:"Минеральные Воды",rating:"4.7",img:"https://images.unsplash.com/photo-1586528116311-ad8dd3c8310d?w=600",desc:"Быстрая доставка документов."},
{id:7,name:"Репетитор английского",cat:"Обучение",price:"от 900 ₽",city:"Москва",rating:"5.0",img:"https://images.unsplash.com/photo-1509062522246-3755977927d7?w=600",desc:"Индивидуальные занятия."},
{id:8,name:"Выгул собак",cat:"Питомцы",price:"от 500 ₽",city:"Минеральные Воды",rating:"4.9",img:"https://images.unsplash.com/photo-1552053831-71594a27632d?w=600",desc:"Прогулки с питомцами."},
{id:9,name:"Фотосессия",cat:"Фото",price:"от 2 000 ₽",city:"Москва",rating:"5.0",img:"https://images.unsplash.com/photo-1516035069371-29a1b244cc32?w=600",desc:"Портретная и семейная съёмка."}
];

const masters=[
["Александр","IT-мастер","4.9","https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=300"],
["Мария","Клининг","4.8","https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=300"],
["Дмитрий","Автоуслуги","4.9","https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?w=300"],
["Анна","Визажист","5.0","https://images.unsplash.com/photo-1534528741775-53994a69daeb?w=300"]
];

let favorites=JSON.parse(localStorage.getItem("ryadom_favorites")||"[]");
let orders=JSON.parse(localStorage.getItem("ryadom_orders")||"[]");
let selected="Все";
let city="Минеральные Воды";

function save(){
localStorage.setItem("ryadom_favorites",JSON.stringify(favorites));
localStorage.setItem("ryadom_orders",JSON.stringify(orders));
}

function card(s){
return `<article class="card">
<img class="card-img" src="${s.img}" onerror="this.src='https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=600'">
<div class="card-body">
<div class="rating">⭐ ${s.rating}</div>
<h3>${s.name}</h3>
<div class="price">${s.price}</div>
<div class="location">⌖ ${s.city}</div>
<div class="card-bottom">
<button class="heart ${favorites.includes(s.id)?"liked":""}" onclick="favorite(${s.id})">${favorites.includes(s.id)?"♥":"♡"}</button>
<button class="arrow" onclick="detail(${s.id})">→</button>
</div>
</div></article>`;
}

function render(){
let q=document.getElementById("search").value.toLowerCase();
let list=services.filter(s=>(selected==="Все"||s.cat===selected)&&(!q||(s.name+s.cat+s.desc).toLowerCase().includes(q)));
document.getElementById("homeCards").innerHTML=list.slice(0,6).map(card).join("");
document.getElementById("catalogCards").innerHTML=list.map(card).join("")||'<div class="empty">Ничего не найдено</div>';
document.getElementById("catalogTitle").textContent=selected==="Все"?"Все предложения":selected;
document.getElementById("favoriteCards").innerHTML=services.filter(s=>favorites.includes(s.id)).map(card).join("")||'<div class="empty">Избранное пока пустое ♡</div>';
document.getElementById("orderList").innerHTML=orders.map(o=>`<div class="order"><h3>${o.title}</h3><p>${o.desc}</p><b>📍 ${o.city}</b><p><button class="btn secondary" onclick="toast('Отклик скоро появится')">Откликнуться</button></p></div>`).join("")||'<div class="empty">Пока нет объявлений. Создай первое!</div>';
}

function fillCategories(id){
document.getElementById(id).innerHTML=categories.map(c=>`<button class="category ${selected===c[1]?"selected":""}" onclick="choose('${c[1]}')"><span>${c[0]}</span><b>${c[1]}</b></button>`).join("");
}

function choose(c){
selected=c;fillCategories("categories");fillCategories("catalogCategories");render();go("catalog");
}

function favorite(id){
favorites.includes(id)?favorites=favorites.filter(x=>x!==id):favorites.push(id);
save();render();toast("Избранное обновлено");
}

function detail(id){
let s=services.find(x=>x.id===id);
alert(s.name+"\n\n"+s.desc+"\n\nЦена: "+s.price+"\nГород: "+s.city+"\n\nДемо-карточка услуги.");
}

function go(id){
document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
document.getElementById(id).classList.add("active");
document.querySelectorAll(".menu button").forEach(b=>b.classList.remove("active"));
render();
if(id==="masters")renderMasters();
window.scrollTo({top:0,behavior:"smooth"});
}

function renderMasters(){
document.getElementById("masterCards").innerHTML=masters.map(m=>`<article class="card"><img class="card-img" src="${m[3]}"><div class="card-body"><h3>${m[0]}</h3><p>${m[1]}</p><div class="rating">⭐ ${m[2]}</div><button class="btn primary" onclick="toast('Чаты подключим позже')">Написать</button></div></article>`).join("");
}

function openOrder(){document.getElementById("orderModal").classList.add("show")}
function closeOrder(){document.getElementById("orderModal").classList.remove("show")}

function publishOrder(e){
e.preventDefault();
orders.unshift({title:newTitle.value,cat:newCategory.value,city:newCity.value,desc:newDescription.value});
save();render();closeOrder();go("orders");toast("Объявление опубликовано!");
e.target.reset();
}

function searchHero(){
search.value=heroSearch.value;render();go("catalog");
}

function setCity(c){city=c;toast("Выбран город: "+c)}

function saveProfile(e){
e.preventDefault();
profileTitle.textContent=profileName.value;
toast("Профиль обновлён!");
}

let timer;
function toast(t){
let el=document.getElementById("toast");
el.textContent=t;el.style.display="block";
clearTimeout(timer);timer=setTimeout(()=>el.style.display="none",2500);
}

fillCategories("categories");
fillCategories("catalogCategories");

filters.innerHTML=["Все","Ремонт","Уборка","Красота","IT","Доставка","Авто"].map(x=>`<button class="filter ${x==="Все"?"active":""}" onclick="choose('${x}')">${x}</button>`).join("");

orderModal.addEventListener("click",e=>{if(e.target.id==="orderModal")closeOrder()});
render();
</script>
</body>
</html>
