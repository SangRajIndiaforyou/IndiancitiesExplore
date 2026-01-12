<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IndiaForYou - Discover India</title>
    <style>
        html { scroll-behavior: smooth; }
        body {
            font-family: Arial, sans-serif;
            margin: 0; padding: 0;
            background-color: #f9f9f9; color: #333;
        }
        nav {
            background-color: #FF9933; color: white;
            padding: 1rem; box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            position: sticky; top: 0; z-index: 100;
        }
        nav ul { list-style: none; margin: 0; padding: 0; display: flex; justify-content: center; }
        nav li { margin: 0 1rem; }
        nav a { color: white; text-decoration: none; font-weight: bold; transition: color 0.3s ease, transform 0.3s ease; }
        nav a:hover { color: #128807; transform: scale(1.1); }

        .hero {
            background: linear-gradient(to right, #FF9933, #FFFFFF, #128807);
            height: 60vh; display: flex; align-items: center; justify-content: center; text-align: center;
            color: #333; padding: 0 1rem;
        }
        .hero h1 { font-size: 3rem; margin: 0; color: #FF9933; transition: color 0.3s ease; }
        .hero h1:hover { color: #128807; }
        .hero p { font-size: 1.5rem; color: #128807; }

        .cities { padding: 2rem; text-align: center; background-color: #FFFFFF; }
        .cities h2 { margin-bottom: 2rem; color: #FF9933; transition: color 0.3s ease; }
        .cities h2:hover { color: #128807; }

        .card-container { display: flex; flex-wrap: wrap; justify-content: center; gap: 1rem; }
        .card {
            background-color: #FFFFFF; border: 2px solid #128807; border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1); width: 250px; overflow: hidden; text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .card:hover { transform: translateY(-10px); box-shadow: 0 8px 16px rgba(0,0,0,0.2); }
        .card img { width: 100%; height: 150px; object-fit: cover; transition: transform 0.3s ease; }
        .card:hover img { transform: scale(1.05); }
        .card h3 { margin: 1rem 0; color: #FF9933; transition: color 0.3s ease; }
        .card h3:hover { color: #128807; }
        .card p { padding: 0 1rem; margin-bottom: 1rem; color: #333; }
        .card button {
            background-color: #128807; color: white; border: none;
            padding: 0.5rem 1rem; cursor: pointer; margin-bottom: 1rem; border-radius: 4px; font-weight: bold;
            transition: background-color 0.3s ease, transform 0.3s ease;
        }
        .card button:hover { background-color: #FF9933; transform: scale(1.05); }

        /* Modal Styles */
        .modal { display: none; position: fixed; z-index: 1; left: 0; top: 0; width: 100%; height: 100%; overflow: auto; background-color: rgba(0,0,0,0.4); }
        .modal-content { background-color: #fefefe; margin: 15% auto; padding: 20px; border: 1px solid #888; width: 80%; max-width: 600px; border-radius: 8px; }
        .close { color: #aaa; float: right; font-size: 28px; font-weight: bold; cursor: pointer; }
        .close:hover { color: black; transform: scale(1.2); }
        .tabs { display: flex; justify-content: center; margin-bottom: 1rem; }
        .tab-button {
            background-color: #FFFFFF; border: 2px solid #128807; color: #128807;
            padding: 0.5rem 1rem; cursor: pointer; border-radius: 4px 4px 0 0; font-weight: bold; margin: 0 0.2rem;
        }
        .tab-button:hover { background-color: #128807; color: white; }
        .tab-button.active { background-color: #128807; color: white; }
        .tab-content { display: none; padding: 1rem; border: 2px solid #128807; border-radius: 0 4px 4px 4px; background-color: #f9f9f9; }
        .tab-content.active { display: block; }
        .tab-content ul { list-style: none; padding: 0; }
        .tab-content li { margin: 0.5rem 0; }

        @media (max-width: 768px) {
            nav ul { flex-direction: column; align-items: center; }
            nav li { margin: 0.5rem 0; }
            .hero h1 { font-size: 2rem; }
            .hero p { font-size: 1.2rem; }
            .card-container { flex-direction: column; align-items: center; }
            .card { width: 90%; max-width: 300px; }
            .tabs { flex-wrap: wrap; }
            .tab-button { flex: 1 1 45%; margin: 0.2rem; }
        }
        @media (max-width: 480px) {
            .hero { height: 50vh; }
            .hero h1 { font-size: 1.8rem; }
            .hero p { font-size: 1rem; }
            .tab-button { flex: 1 1 100%; }
        }
    </style>
</head>
<body>
    <nav>
        <ul>
            <li><a href="#home">Home</a></li>
            <li><a href="#destinations">Destinations</a></li>
        </ul>
    </nav>

    <section class="hero" id="home">
        <div>
            <h1>Welcome to IndiaForYou</h1>
            <p>Explore the vibrant culture, stunning landscapes, and rich heritage of India.</p>
        </div>
    </section>

    <section class="cities" id="destinations">
        <h2>Explore Indian Cities</h2>
        <div class="card-container">
            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/India_Gate_in_New_Delhi_03-2016_img3.jpg/320px-India_Gate_in_New_Delhi_03-2016_img3.jpg" alt="Delhi">
                <h3>Delhi</h3>
                <p>The capital city, blending ancient history with modern vibrancy.</p>
                <button class="explore-btn" data-city="Delhi">Explore</button>
            </div>
            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Mumbai_skyline_at_sunset.jpg/320px-Mumbai_skyline_at_sunset.jpg" alt="Mumbai">
                <h3>Mumbai</h3>
                <p>The bustling metropolis known for Bollywood and its iconic skyline.</p>
                <button class="explore-btn" data-city="Mumbai">Explore</button>
            </div>
            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fc/Bangalore_skyline.jpg/320px-Bangalore_skyline.jpg" alt="Bangalore">
                <h3>Bangalore</h3>
                <p>The Silicon Valley of India, famous for tech and lush gardens.</p>
                <button class="explore-btn" data-city="Bangalore">Explore</button>
            </div>
            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Marina_Beach_Chennai.jpg/320px-Marina_Beach_Chennai.jpg" alt="Chennai">
                <h3>Chennai</h3>
                <p>A coastal city rich in culture, temples, and South Indian cuisine.</p>
                <button class="explore-btn" data-city="Chennai">Explore</button>
            </div>
            <div class="card">
                <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/00/Kolkata_Market.jpg/320px-Kolkata_Market.jpg" alt="Kolkata">
                <h3>Kolkata</h3>
                <p>The cultural capital, home to colonial architecture and festivals.</p>
                <button class="explore-btn" data-city="Kolkata">Explore</button>
            </div>
        </div>
    </section>

    <!-- Modal -->
    <div id="cityModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <h2 id="modalTitle"></h2>
            <div class="tabs">
                <button class="tab-button active" data-tab="food">Food</button>
                <button class="tab-button" data-tab="sightseeing">Sightseeing</button>
                <button class="tab-button" data-tab="temples">Temples</button>
                <button class="tab-button" data-tab="shopping">Shopping</button>
            </div>
            <div id="food" class="tab-content active"><ul id="foodList"></ul></div>
            <div id="sightseeing" class="tab-content"><ul id="sightseeingList"></ul></div>
            <div id="temples" class="tab-content"><ul id="templesList"></ul></div>
            <div id="shopping" class="tab-content"><ul id="shoppingList"></ul></div>
        </div>
    </div>

    <script>
        const citiesData = [
            { name: "Delhi", food: ["Butter Chicken","Chole Bhature","Paratha","Lassi"], sightseeing:["Red Fort","India Gate","Qutub Minar","Lotus Temple"], temples:["Akshardham Temple","Lakshmi Narayan Temple","Siddhivinayak Temple"], shopping:["Chandni Chowk","Connaught Place","Karol Bagh"] },
            { name: "Mumbai", food:["Vada Pav","Pav Bhaji","Bhel Puri","Fish Curry"], sightseeing:["Gateway of India","Marine Drive","Elephanta Caves","Chhatrapati Shivaji Terminus"], temples:["Siddhivinayak Temple","Mahalaxmi Temple","Mount Mary Church"], shopping:["Colaba Causeway","Crawford Market","Linking Road"] },
            { name: "Bangalore", food:["Masala Dosa","Biryani","Filter Coffee","Ragi Mudde"], sightseeing:["Bangalore Palace","Cubbon Park","Lalbagh Botanical Garden","Vidhana Soudha"], temples:["Bull Temple","ISKCON Temple","Gavi Gangadhareshwara Temple"], shopping:["Commercial Street","Brigade Road","UB City"] },
            { name: "Chennai", food:["Idli Sambar","Dosa","Chettinad Chicken","Pongal"], sightseeing:["Marina Beach","Kapaleeshwarar Temple","Fort St. George","Valluvar Kottam"], temples:["Kapaleeshwarar Temple","Parthasarathy Temple","Ashtalakshmi Temple"], shopping:["T. Nagar","Pondy Bazaar","Express Avenue"] },
            { name: "Kolkata", food:["Rosogolla","Mutton Biryani","Puchka","Mishti Doi"], sightseeing:["Victoria Memorial","Howrah Bridge","Kolkata Maidan","St. Paul's Cathedral"], temples:["Kali Temple","Dakshineswar Kali Temple","Belur Math"], shopping:["New Market","Gariahat","Camac Street"] }
        ];

        const modal = document.getElementById('cityModal');
        const modalTitle = document.getElementById('modalTitle');
        const foodList = document.getElementById('foodList');
        const sightseeingList = document.getElementById('sightseeingList');
        const templesList = document.getElementById('templesList');
        const shoppingList = document.getElementById('shoppingList');
        const closeBtn = document.getElementsByClassName('close')[0];
        const tabButtons = document.querySelectorAll('.tab-button');
        const tabContents = document.querySelectorAll('.tab-content');

        document.querySelectorAll('.explore-btn').forEach(button => {
            button.addEventListener('click', function() {
                const cityName = this.getAttribute('data-city');
                const city = citiesData.find(c => c.name === cityName);
                if(city){
                    modalTitle.textContent = city.name;
                    fillList(foodList, city.food);
                    fillList(sightseeingList, city.sightseeing);
                    fillList(templesList, city.temples);
                    fillList(shoppingList, city.shopping);
                    modal.style.display='block';
                    showTab('food');
                }
            });
        });

        function fillList(list, items){ list.innerHTML=''; items.forEach(i=>{ let li=document.createElement('li'); li.textContent=i; list.appendChild(li); }); }
        tabButtons.forEach(b=>{ b.addEventListener('click',()=>showTab(b.getAttribute('data-tab'))); });
        function showTab(id){ tabContents.forEach(c=>c.classList.remove('active')); tabButtons.forEach(b=>b.classList.remove('active')); document.getElementById(id).classList.add('active'); document.querySelector(`[data-tab="${id}"]`).classList.add('active'); }
        closeBtn.onclick = ()=>modal.style.display='none';
        window.onclick = e=>{ if(e.target===modal) modal.style.display='none'; };
    </script>
</body>
</html>
