<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Социальные сети Zloretsky</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet" />
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            font-family: 'Roboto', sans-serif;
            position: relative;
        }

        h1 {
            color: white;
            text-align: center;
            font-size: 3em;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
            margin-bottom: 20px;
        }

        .instruction {
            color: white;
            text-align: center;
            font-size: 1.5em;
            margin-bottom: 10px;
            padding: 15px 30px;
            border-radius: 25px;
            background-color: rgba(255, 255, 255, 0.3);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        }

        .reward {
            color: white;
            text-align: center;
            font-size: 1.2em;
            margin-bottom: 20px;
        }

        .socials-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 30px;
        }

        .button {
            padding: 15px 30px;
            border-radius: 25px;
            color: white;
            background-color: #007bff;
            border: none;
            cursor: pointer;
            text-decoration: none;
            display: flex;
            justify-content:center ;
             align-items:center ;
             position :relative ;
             overflow :hidden ;
             font-size :1.2em ;
             transition :transform .2s ease , background-color .3s ease ;
             margin-bottom :15px ;
         }
 
         .button img {
             width :24px ;
             height :auto ;
             margin-right :10px ;
         }
 
         .button:hover {
             transform :scale(1.05) ;
             background-color :#0056b3 ;
         }
 
         footer {
             position :absolute ;
             bottom :10px ;
             color :white ;
             font-size :.8em ;
         }
 
         footer a {
             color :#00ffcc ;
             text-decoration :none ;
         }
 
         footer a:hover {
             text-decoration :bold ;
         }
 
         .train {
             position :absolute ;
             bottom :-100px ;
             left :-200px ;
             width :200px ;
             animation :moveTrain linear infinite ;
         }
 
         @keyframes moveTrain {
             from { transform :translateX(0) ; }
             to { transform :translateX(100vw) ; }
         }
 
         .background {
             position :absolute ;
             top :0 ;
             left :0 ;
             width :100vw ;
             height :100vh ;
             z-index :-1 ;
             background-color :rgba(128 ,0 ,128 ,0.5) ;
             animation :rgbEffect 5s infinite alternate ;
         }
 
         @keyframes rgbEffect {
               0% { background-color  rgba(128, 0, 128, 0.5); }
               50% { background-color  rgba(255, 0, 255, 0.5); }
               100% { background-color  rgba(75, 0, 130, 0.5); }
          }
 
          .circle {
              position:absolute ;
              border-radius :50% ;
              opacity :.7 ;
              pointer-events:auto ; /* Чтобы можно было кликать */
          }
     </style>
 </head>
 <body>
     <div class="background"></div>

     <h1>Добро пожаловать на мой сайт!</h1>
     <div class="instruction">Вы можете лопать эти ебаные круги</div>
     <div class="reward">Если ты лопнешь <strong>15 шариков</strong>, я скину <strong>50 рублей</strong></div>

     <div class="socials-container">
         <a href="https://t.me/Zloretsky_traffic" class="button" target="_blank">
           <img src="https://upload.wikimedia.org/wikipedia/commons/8/88/Telegram_logo.svg" alt="" /> Телеграм @Zloretsky_traffic
         </a>

         <a href="https://discord.com/users/papadzhi" class="button" target="_blank">
           <img src="https://upload.wikimedia.org/wikipedia/en/7/7c/Discord_logo.svg" alt="" /> Discord @papadzhi
         </a>

         <a href="https://nursultan.fun/" class="button" target="_blank">
           <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Nursultan_%28city%29_logo.svg/1200px-Nursultan_%28city%29_logo.svg.png" alt="" /> Бесплатный Nursultan
         </a>
     </div>

     <!-- Поезд -->
     <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Train_icon.svg/1200px-Train_icon.svg.png" alt="" class="train" />

     <footer>&copy;2023 Все права защищены.</footer>

     <script>
       let popCount = 0;

       function createCircle() {
           const circle = document.createElement('div');
           circle.className = 'circle';

           const size = Math.random() * (100 -20) +20; // от20 до100 px
           circle.style.width = `${size}px`;
           circle.style.height = `${size}px`;

           circle.style.backgroundColor = `rgba(255,255,255,${Math.random() * (1 - .3) + .3})`;

           circle.style.top = `${Math.random() * window.innerHeight}px`;
           circle.style.left = `${Math.random() * window.innerWidth}px`;

           document.body.appendChild(circle);

           circle.addEventListener('click', () => {
               popCount++;
               circle.remove();
               createCircle();

               if (popCount ===10) { // Изменено на проверку на количество лопнувших кружков
                   window.open('https://parad1st.github.io/Screamer/', '_blank'); // Открываем ссылку на скример
               }

               // Эффект "лопания"
               const burstEffect = document.createElement('div');
               burstEffect.style.position = 'absolute';
               burstEffect.style.width = '50px';
               burstEffect.style.height = '50px';
               burstEffect.style.backgroundColor = 'rgba(255,255,255,1)';
               burstEffect.style.borderRadius = '50%';
               burstEffect.style.top = `${circle.offsetTop + size /2 -25}px`;
               burstEffect.style.left = `${circle.offsetLeft + size /2 -25}px`;
               document.body.appendChild(burstEffect);

               setTimeout(() => burstEffect.remove(),300);
           });
       }

       for(let i=0; i<10; i++) createCircle();
     </script>
 </body>
 </html>
