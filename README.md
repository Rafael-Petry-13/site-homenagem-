<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Para Vocês Duas, Meu Mundo</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;600;700;800&family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,500&family=Poppins:wght@300;400;500;600&display=swap');

  * { margin:0; padding:0; box-sizing:border-box; }

  :root{
    --roxo-escuro:#4a2c6d;
    --roxo:#7b4ba3;
    --roxo-claro:#b98fd6;
    --lilas:#e6d5f5;
    --lilas-suave:#f3eafb;
    --branco:#ffffff;
    --texto:#3a2a4d;
  }

  html{ scroll-behavior:smooth; }

  body{
    font-family:'Poppins', sans-serif;
    color:var(--texto);
    background:linear-gradient(180deg, #ffffff 0%, #f7f0fc 40%, #efe1fa 100%);
    overflow-x:hidden;
  }

  /* ---------- decoração de fundo ---------- */
  .bg-decor{
    position:fixed; inset:0; pointer-events:none; z-index:0; overflow:hidden;
  }
  .bg-decor span{
    position:absolute; border-radius:50%;
    background:radial-gradient(circle at 30% 30%, var(--lilas) 0%, transparent 70%);
    opacity:.5; filter:blur(2px);
  }
  .bg-decor span:nth-child(1){ width:300px; height:300px; top:-80px; left:-80px; }
  .bg-decor span:nth-child(2){ width:220px; height:220px; top:40%; right:-100px; }
  .bg-decor span:nth-child(3){ width:180px; height:180px; bottom:-60px; left:20%; }

  section{ position:relative; z-index:1; }

  /* ---------- hero ---------- */
  .hero{
    min-height:100vh;
    display:flex; flex-direction:column; align-items:center; justify-content:center;
    text-align:center;
    padding:40px 20px;
  }
  .hero .eyebrow{
    font-family:'Cormorant Garamond', serif;
    font-style:italic;
    font-size:1.3rem;
    color:var(--roxo);
    letter-spacing:2px;
    margin-bottom:18px;
    opacity:0;
    animation:fadeUp 1s ease forwards .2s;
  }
  .hero h1{
    font-family:'Playfair Display', serif;
    font-weight:800;
    font-size:clamp(2.4rem, 7vw, 4.6rem);
    line-height:1.15;
    background:linear-gradient(120deg, var(--roxo-escuro), var(--roxo) 50%, var(--roxo-claro));
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
    opacity:0;
    animation:fadeUp 1s ease forwards .5s;
  }
  .hero .sub{
    margin-top:22px;
    max-width:620px;
    font-size:1.1rem;
    line-height:1.8;
    color:#5c4570;
    font-weight:300;
    opacity:0;
    animation:fadeUp 1s ease forwards .9s;
  }
  .hero .assinatura{
    margin-top:32px;
    font-family:'Cormorant Garamond', serif;
    font-style:italic;
    font-size:1.4rem;
    color:var(--roxo-escuro);
    opacity:0;
    animation:fadeUp 1s ease forwards 1.3s;
  }
  .scroll-hint{
    margin-top:60px;
    font-size:.8rem;
    letter-spacing:3px;
    text-transform:uppercase;
    color:var(--roxo-claro);
    opacity:0;
    animation:fadeUp 1s ease forwards 1.7s, bounce 2s ease-in-out infinite 2.7s;
  }

  @keyframes fadeUp{
    from{ opacity:0; transform:translateY(24px); }
    to{ opacity:1; transform:translateY(0); }
  }
  @keyframes bounce{
    0%,100%{ transform:translateY(0); }
    50%{ transform:translateY(8px); }
  }

  /* ---------- divisor ---------- */
  .divisor{
    display:flex; align-items:center; justify-content:center; gap:14px;
    padding:10px 20px 60px;
  }
  .divisor .linha{ width:60px; height:1px; background:var(--roxo-claro); }
  .divisor .flor{ color:var(--roxo); font-size:1.3rem; }

  /* ---------- galeria ---------- */
  .galeria-intro{
    text-align:center; padding:0 24px 40px;
  }
  .galeria-intro h2{
    font-family:'Playfair Display', serif;
    font-weight:700;
    font-size:clamp(1.8rem, 4vw, 2.6rem);
    color:var(--roxo-escuro);
  }
  .galeria-intro p{
    margin-top:14px;
    color:#6a5480;
    font-size:1rem;
    max-width:520px;
    margin-left:auto; margin-right:auto;
    line-height:1.7;
    font-weight:300;
  }

  .galeria{
    max-width:1100px;
    margin:0 auto;
    padding:0 24px 100px;
    display:grid;
    grid-template-columns:repeat(auto-fit, minmax(260px, 1fr));
    gap:28px;
  }
  .card{
    background:var(--branco);
    border-radius:20px;
    overflow:hidden;
    box-shadow:0 10px 30px rgba(123,75,163,.15);
    transition:transform .4s ease, box-shadow .4s ease;
    opacity:0; transform:translateY(30px);
  }
  .card.mostrar{ animation:fadeUp .8s ease forwards; }
  .card:hover{
    transform:translateY(-8px);
    box-shadow:0 18px 40px rgba(123,75,163,.28);
  }
  .card .img-wrap{ position:relative; overflow:hidden; aspect-ratio:4/5; }
  .card img{
    width:100%; height:100%; object-fit:cover;
    display:block;
    transition:transform .6s ease;
  }
  .card:hover img{ transform:scale(1.06); }
  .card .legenda{
    padding:18px 20px 22px;
    font-family:'Cormorant Garamond', serif;
    font-style:italic;
    font-size:1.15rem;
    color:var(--roxo-escuro);
    text-align:center;
  }

  /* card grande em destaque */
  .card.destaque{ grid-column:span 2; }
  @media (max-width:640px){
    .card.destaque{ grid-column:span 1; }
  }

  /* ---------- carta ---------- */
  .carta{
    max-width:700px;
    margin:0 auto;
    padding:60px 30px 120px;
    text-align:center;
  }
  .carta .aspas{
    font-family:'Playfair Display', serif;
    font-size:3.5rem;
    color:var(--roxo-claro);
    line-height:1;
    margin-bottom:10px;
  }
  .carta h2{
    font-family:'Playfair Display', serif;
    font-weight:700;
    font-size:clamp(1.6rem, 3.6vw, 2.2rem);
    color:var(--roxo-escuro);
    margin-bottom:24px;
  }
  .carta p{
    font-family:'Cormorant Garamond', serif;
    font-size:1.35rem;
    line-height:2;
    color:#4c3a63;
  }
  .carta p + p{ margin-top:20px; }
  .carta .assinatura-final{
    margin-top:36px;
    font-family:'Cormorant Garamond', serif;
    font-style:italic;
    font-size:1.5rem;
    color:var(--roxo);
  }

  /* ---------- rodape ---------- */
  footer{
    text-align:center;
    padding:40px 20px 50px;
    color:var(--roxo-claro);
    font-size:.85rem;
    letter-spacing:1px;
  }
  footer .coracao{ color:var(--roxo); }
</style>
</head>
<body>

<div class="bg-decor"><span></span><span></span><span></span></div>

<section class="hero">
  <div class="eyebrow">uma pequena homenagem, feita com o maior amor</div>
  <h1>Para as duas mulheres<br>que são o meu mundo</h1>
  <p class="sub">
    Cada foto aqui guarda um pedacinho da nossa história. Vocês duas são o motivo
    de eu querer ser um homem melhor todos os dias.
  </p>
  <div class="assinatura">com todo o meu amor, Rafael</div>
  <div class="scroll-hint">role para ver &#9662;</div>
</section>

<div class="divisor"><span class="linha"></span><span class="flor">&#10047;</span><span class="linha"></span></div>

<section class="galeria-intro">
  <h2>Nossos momentos</h2>
  <p>Pequenos instantes que, juntos, contam a maior das histórias: a nossa família.</p>
</section>

<section class="galeria">
  <div class="card destaque">
    <div class="img-wrap"><img src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAAAAAAD/2wBDAAcFBQYFBAcGBgYIBwcICxILCwoKCxYPEA0SGhYbGhkWGRgcICgiHB4mHhgZIzAkJiorLS4tGyIyNTEsNSgsLSz/2wBDAQcICAsJCxULCxUsHRkdLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCz/wAARCAOEAqMDASIAAhEBAxEB/8QAHAAAAgIDAQEAAAAAAAAAAAAAAwQCBQABBgcI/8QARxAAAgEDAwIFAQUHAwMEAAILAQIDAAQRBRIhMUEGEyJRYXEHFDKBkRUjQlKhscEz0eEkQ3IWYvDxghclUzWSCDRFY6Kywv/EABoBAAMBAQEBAAAAAAAAAAAAAAABAgMEBQb/xAAmEQEBAQEAAwEBAAIDAAMBAQAAARECAyExEkEEURMiYRQycUKB/9oADAMBAAIRAxEAPwCdxLtOF6Go28QwWGcUrNNmfOeM0/EwFqf4TnNcjpzIGlzifBPA4rrdOl2W/ODkZri4R/1QBAOTXQW1yUTbnjpRLhWLWVt8hPXNHiTyosn86Wsx5zcdKZumCw7QaZYq7hzLN7gUzEwjjJPSgRR5nyPzqdy6quAefakeItLulyvOasFdY4Bng44FV0CerNTnm3ShQeBRoMQM0kv51ZyyCOMKv4mpCyX0F+9RmlZpxznFLTxY2Y3SY7CnLmQCPYDzQLIBE3dzQpn3yk/NG+hg9rFulJPRa1qEmPQPqaahURwZPWkZB58vB6nFV/MT9otlGQpduPal55DJMwzxTs7+TbY79KRiXzJgO2aX/hw7AvlWxPfGaQVWkl9VP3LCOIKD+KgWabpjnpTogt0AlqQvcUpAn4iey0e7PqC5oQ/d2xLfxGlb7E+EpFD5pKRChOFJqwRRtzg47CpGJSpI4OKys1tzcU4fzGIXIHckURoIZoWjlQSKeobkGnDbjyxjjA6UtKmxgQSD0I96n3G0srjde+zbStRdpdNH7OnxnCcxsfkdvqK801rw7qnh9i17bMIQcecnqT9e3517yWKsSKgrLKJEkRXRuCrDIP1Fdfj/AMvrj1fcc/k/xee/nqvnZXz0oq816vrn2Z6XqJefTidOuG5wPVGT/wCPb8q881Tw1q2huRfWjJHnAmT1Rt9D/vXpeLz8eSeq8vy/4/fj+xXqKIKiBjrU1rpcnxojIqvvbUSKTjmrLFRdAVPFTeZZh8dfmuX9dvL6Scg8V3/grxkLcrbXQ3LnKk84Ncne2QYFgOarIWaCfPIINcd5/NyuyWdTY+ntJ1FJ1DKQQQDVh97WQlFOWryb7P8AxYG/6O8cZIxG3+K7xJ5/OC28e5j0JGQPrRmFPZ+6huZAcbeegzzQ4NII9dw2c/wigmWeO+t4JGy8h9Rq8lIxgUlfEIUSIAIoUDtTKyZakWbHepwyZNAWiSdqIGGSDyDSIlxU1l96CV1/4N0m/u3umiaOR/xbDgE++Kr7nwgUz9zl3YHCuMH9a6hJeMVrz8HOKMP9Y85urWaznMU0bI/seh+hpcwyufShNekXUVtqMLQSqCSOD3U+4rlLnR9StpWVJIXAPGTtJFTjSXVPFprnl/TmmYreOBiWBYUyLbU0IDwIf/xCmFgux+O23A9hg0jKh4x7D/FS8xfejyRKmPOgMefes+6QOvoamCxxyaC575rdz5lq20+ofFV1xqHl/wDbNB4byQTgVsIzDJ4qo/a7dAlZ+0Z3PWkS32IfxHFFQxx9DVQJ3ceo80RGJ/iNVCq5juEBGGFOpOhXJIGKoU9A3EAD3oM+oEgqpwtaSsry6F9ThjJAIJHzQjrTNxvH5Vx81xKc4zSy3EqtkEg1UZ3l3tvqDSnGcinYr6OL8ZrhrbVXThuDTMWps8u5ug+auMrK76G8VjwKdSXNcrZajGQMH9auYb+Jh+IVUZrXIIokfBFJJchhxg0eOTPNVidWiLuXiiJHjik4LkggGnVnXFPCGVTjiotESeTU0YsOKwk0YWg7AprauFPIqTChstPC1J3RhwKq76Hqyg4p7aQTWOm5CKMLVCqYbIqwil2xjnmgvA6tWJBITnPFAblkLc9q1BIVGB2phYSUwcVDyQpOPajA0JG3HmiiQ4xmgoG3cjOaKPnijADMpkfJPArZIUDFTdAxrcUWWGegoOJCBiM4rKsFiXbzWVKnkCRLPLg9OtEnKpGE3HBPvQ7Zs5x1xQZm805zjBrw30MNW0e4hgxwD3qyt5A0mAcgHFVALQW5OeaNpjvJIBF+I8nJ4pCuzscRx8msupN8gx0FJicxqAT2oqSI0ijd1poTGUDN8UjI/mT5J70xfzmOLauCW4qvhSZpg3bvmlTWobEGfilk/eSYHWlLm/O/yI8jBwSaNpsyyXJKnJ6Z7fSg5PWrff8Ad7bBpe3kMsuT2rdyxYbGGCKjaoUJPb3pURavdCODaO9StkMsi+w5qokkzKck4FXVg4EYJ7iifSNXkm2EgHk0CwU7yT2qEswuHOw8ZxTUQEUGM80y/gV9KGygPSt2K5jL0qEJkIPO41YemC2OwfQU5T/mFrqXMgHtxTUG2KMO2ACKRhiEsuGPU09ehVtwB74FG/0f+EZmMspZMnJqN44cRwjqRzRrdF8zp+Hk0qxWectkh89qnTkEC4XHX2rQ5JStITFgOc5qTDuBSWigKqV67Tj8qFPEJBnuOaKJArkPjkdqmUznb+lIfFRPARkDkN0NK+pD7Yq4SMi5kUnIUDFCnsAx3Ln6VNjbnv8A2r1nA61NhFcRNFLGksbjDI4yCPkUG4tmjc9eKEJGTnPSp2xrkrmdf+zOzvd0+kSCxnPPlHmJj/da891TR9Q0OcQ6jbPAT+FjyjfRuhr2+C8yeTRbmO11C0a3uYknhcYKOuRXb4f8zrn117cPm/wue/fPqvn8NxUgciu/8QfZqdj3GhsDzn7q55+in/Brgprea0uWt7iJ4ZV6o64Ir1fH5ePJN5rxvJ4e/Hc6gcke5eKqb+0O3eBgirntQZlDJgiq75/UHj6sqk02+ezuldTgqcivY/BXjP8AacnkXRVZQMhh/EK8YvbUwS7wPTT+i6k9jcLKjFWXoa5Pfyur/wBj6FDJNdC6JHp4Xmn2Ep6bR9TXGaBq/wC3bKMRkBlA310d1dNE4yMk0gdNvO4O11+ua0EeM+ojI9qQjv5QPQjn4Ao6NdT5xBIvy3FAOCUipifj3paO0uS2WAA+tMpZtu5YfnQQ0Dsx6cUx5bFeelQSPy+M5ovmbhigsBSPbLkGo61Zi601pFz5sQ3AijpGAc5OaMHG0gjig3ByaiVUZY5+tbttQfzCQx6e9a1SxWO6LpjDMf70rCoWUjGWK9B3ow4Y1zVlt/uKySAF0YjPHeo2l+HAxXn32laxjxNBaRv/APyluqOB2Y8kf2qXhzxSiqIrmTBHCtmpax6b5m4ZIzQJbSCbrEtV1prlrOu1ZRkd81lzrVpbjLTqT7A0GbGg2zjp/WtNoAUfucZ+TXOzeNoY8hZPpij6N4iuNavzBC5VEGXb2FIl5b6KrTASvn4WultLSK2hwkS+3Sq2zCiQYyfkmry2G7JJ4FOe02tLpljLGVe0jOeuV61S6h4WsHkzbZt2/kzlT/tV5PqMVsuMg1S3+rQ3DeVGPUx4zVo1V/sm1iZo3RldeCDVfdaZECcL0roklFxthdcvt9Lf4NAMSEndir5RXItpcrTDGQueTjtRZNP2AFGrqJIkK4AxSDWjMSFrSMbVNHNNEpUn6GrGyuJIwGlckmmU0hyNzgfFORaC0i/iU/NVEUW31QgDHqFW1pfb+GPNVUfh/wAps7/ypy2sDG/DE/lVM12kuRTVvId/NIQxFeaciBzxTJbRy7RRA24ZpCIsDyeKMrlT8UJGLVoHIPNZ+IVHpmmTK2o5qG4dKlG2TQGeSM5NRMYApjFaKgigALGAKgYvVnpTO3C0Mg4oBV1AfI7UJzlqM59Rpd+tAYMA01boWbpxS0KF2zjinVIVcA0HBwnHWspfzPk1lLFPJMeVGe1IIWMwxzzT18+0YpWLgZrwn0Il3P8AulXpk0zoknl7z79Kq7t8yAZpi0kKQkDg9jSH8dUk4lfbnp1p1EDYIJDL3Fc9YXBd1yMNnrVy17HDExaRQcZPBppwKecPcKAcA8ij5ZYshuWPHGcVS2Vw08obB25xuPTFPXt791jQp6txwfj5pHhO7RknKINxMvU/TNXCxxwxgqNrEA81XBQ+qRsehO79AeabvJo/uyq4znBBxx+tBi21y0twyOpVgM59xVwhEdt0/WqGxk8ucqWDoBlT3+lWUl0Hj2A4FBVBYmmkABJOc8VZrL5VuquecdqV04ZLN8YFQvJgZygPSieiWOntls9RnrTdzMFIRT2zSGnsIrbJ75PNa8/zJjg5Apg/ZqXZmbnFTuZssI1NQjcRxerilhJvkBHOam+vRz2srGAbmY/QUDUJCXI/hQU1E4hg9R5xSDus+7B46U/5hDLlbHd038fOKRZgnB3MFz9R80dpmdRAuSIgAT7/ADUHiAIbOc8Gpqo3GVkiwx3HuRWAFWIkcsMD8qDHzNKYwducDPSitGWXcSQ3QKOlJQmxdjMMZNaQYUMD6h1raOrJkce49qmmCpA5oAAw85OcE4xxRgKi8e2QY6HkVDeInIZ8qwyM/wC9OBqeBZFOQM+9U1zaNGWIFXqusi5U59x3FK3k0awvuGR0JpWavjuxzckewbt23vntUY7woeNz/IFMLbG7RSrDYhO4fI9x2oEsDISAd3xWNmfXXzZZp6C8AxuOPrQ9a0ux1qxP3mCKV1Hpc8MPo3aq0TgZV8gg45o8dwGjMcoDA9CDjFVx3eLsR5PHO+crzTXPCN7pX7+Hfc2xPIC+tPqO4+RXPkcc17XBFPbB4VuGeB/UvmLkqc+9c9q/hay1jMkKi1us4Lxj0t9RXreH/Ll9dvF8n+J1PfLy2eESIVIyDVPJEYJCOQO1dZq+j3ujXXkXsPlk/hccq4+D/iqW7t96/Irq6k6mxz8bLlWPhLxHJo2rQz5zHkLIp7r3r3FHg1MwXMEgkjkAKEe1fNo/dtmvR/s48SrbXQsJ5D5cg9H/ALTWFaT69iMoQAZwKwSKehzSbvmPIpKS7aM5FRq8XgGRmpqKpYdYKrh0zTkOpRPjOVzRCWFRPBqIlBHUVsMDVEIje9FXkUARsTwwoibgeeaYcfrytDdSDpzkVW2t3HZia9l5S1jaV/oB0/tXQeLFMUkM+3IcFD/iuA8VXUtj4QLxvte5uFUD3C5J49qVVzHl15cPf6hcXcrFpJ5DISfk5oYDKcg4p+4tYzL5kKlUcZ2/y/FDEBIxtrPGgcV3cRfgkYfnUzfXEmd7k/U1vyPisMGBTCHnue9eqeBNJNjoX3iYET3Z34P8K9hXA+GtGbVdbhgMe6IeuTj+EV7LCk0MoD2ExjXGOMCj6m3FnptscmRsBe2TVhLN5ELY71WXc01/aA2QMLW5DOrDlh1wKSh1QXmn+YrliPSc9auc5GV62hXU7PISSarJhI8wePgqetFupmUg/wBKB54C5x1otVItbeaQIHIG5e+aNcr5+ZoTzxvH+ap47wiTHY8VbWbiKUHBdGGCD7Ucl1PQa7h1bNMQPGO4zQNQ3xPhQNh5UgdRSaTFXGTito57F6xynFbtrsIMdwaBFIGjyDS+71H4NXKzsdBFKsgyaZjeMdsVzsd+UGParGGYyICtOVOLpCh7inYY4+x5qkiYjrT0EmBVJsWyRKelFEHHSkopD2NOwzno3NNKDqUBOOKAXlbpgCrNCrAgAGlrqMDkcUyKZ96nF+Kl3JD4o0R+aCNjpWYoSuaIpJ60Bo96gxUAjNTYE0Ex9STQC0jcnH60uPU+0DjuanO+CQKlbR87utBjwLxRWCjmghiHx80yUHtk0CFieTxWUysUhXOF/M1lT+o1/LxXUJTLPtixgcE1AblgyO3vUobbPO4sCeR7VG5YojRqTuAxivEr3Fd5omcjeN2efijO7In+oPyoCI7jmPnvk4quvZpI5lUgoO3zUqjq9GxLNhnIKj3qwvLuSA7Q6sOmF71yun6gIlGVIfsc9qbW4a6uFYsTuOaBXTWEsZgYovqU9u1B1OSZjGrqMbvxA4xRYpFgs0MKbWTkqP4gfegSOfK8xgJC3IOetMoBPcvbSRSzBlYdGTn+lOvqcVyMxgkAAcDiqm4keR45C23AIAPtW7O9dZ47MfgY/jx2PakbpLNT5BkcbiRxjjioxzs9wFKnFQll8m0IRCAOOtR0rJvFDnrzQJV7C7QqF9qXRfNumfqKjezeXJsBySM1lgTGZC5JDfhPtT+0ljLMsdvt79hQ7L1zDp1zSc1z57Db245pyyURYbOCetBYbvpyEVRxnmh2JYEkjdyKSmvFnuSc5VfSKPFNJb+odDyRSnun8ixubppWWMnAbsKPZBVVjgHA9qpXm+8OJFIIzxinDdfdbJE53O2TR/Q0HcTs4BOSQce1SaaR2AVCEHuOpqMTDcFU53DJo7bQhx0+feoVESWUsFUN35qSoZAG3AitRHOcnqBzWbyANnGT+VASAMc24ABGOMmp42bn3BR168UJ2ZYnBAYN1paGdbgtCNwEZw2R19qDMvMzEEcAjAz9ay7n/dhAuSMMVx0FL3N1DayRhm2jPO49fmlhqE0l4m1VcMp6DGaAaIZlLQLyBzn0mjRt5sHlugAXkjvmhC8McaeauHXI69f9qmJHeZuGWULncR6TTJWlQbszJ6ZGHrjPRj8GgywrPvCHa55KDqKuobeGaJXYbncZ44xS02kwCRn2lJFGQVYjNLqarju8uZNqjSvkk4OME0uvokZGPTn8q66bT18kqigMTziqHUtNuY0yIldsZG05IFY/murnyaTW8ZWK7iVJ6Zqcl6lvD5qqjkEEgHnGfalyVVRgZB6DFc9Jd3LatLFb3CJICAFccH4p8yl1Y63WL60vreKCS3SSOZcvvUMMe1cHrHgfMbTaWxBI3C2kPqI/9p7/AENXMGpra6gkt1afu4m/eBTu69D9M1aTXA1bUgtsQYcBt2Mc/PtXb4/NeI83y+P914fe28kMjBkZSpIZWGCD9KFaXbW86yISCp6ivoTxD4N0zxPYL5+Ib1F2pcovq+h9xXhXiXwrqnhW/wDIvoSEkJ8qZeY5B8H/ABXRz5Z37jLrw9cfXt3g/X4dd0RWeQG4jUK4J5PzVqtp5jkFx9K8F8Ka/No+qJKH/dN6XXvjPWvXV/bMqrc2skEkLeoevnFF+pnx0X7KjVssTiirpkSgtHIT8GpabdvLZxi4C78c/Wjkqj7gwqpSoSgoME1sFuxoc+oWsYJknQY+arJfEVurFYI5J2H8q4/rVpXSu+MDijRyFfxn865xNQ1W7YmC1WJOg3HJow0e6uRuvb+QZ6rGcUEc8RgXOiyNEVd4iHGDn615H45unuNUtrJRiG2hUgDuWGSa9YtNJsbPcq3Ny+4fxNkVzOoeAoL3WJro35ZJTnBTlfgVNac+nmEdixHxWNpzKwz0bvXqA+z62UYXUHH1jFCb7Ps5Uaou3t+65pK15a1owPAz9KGbZy4UDJPAHvXrMH2d2KjNxqbn4SMD+9XOn6H4f0Z/Mt7RZZx/3ZfW3/FGD9KL7OvCNxZWj319CYHlI2K34iv+K9BlukijwMEiquXU9/C5xSN5qCxpjqT2FVGVuoa1rUWnxtOVALkJx3J45qnE9ppyJZpIhYjcxz1z3rWpWx1aExSttTOaXvdLt5BBaphZRgI3+/xV/wAZizq0gLAenGc1WyOxOBXX22k29lphgjLOccsxzz8VQ3FjIkpPl/pWdjXmkl5wKt7CUglX5GOD7UisXrzj8qdtlBJz7URVW5C3EBt24Yj0sexrm7lZYJmSZSrCrl5TtGDyO9GaxOrWjMwHnpwhzjdW3NYWK2wuy8ZA6A4NTuLvL7VHGe1Jw/uJmj27cnBB6g055YzkCqZ4xCQc1bWVztQiqnGDTMDYzzVRnXQwSq45p2I1TW0npFPxSHNVE1bwvzTkbcVWwN0p6M4HWqiD9u+Ceay5YbTQI3walIdzYppVrglif0o0QbGacW2UjmtiEDpQEEIUUZMEUFxtz70IylaCOEqB1pWV85AoZlLL3pWaUsxQZHuaAGR5shCjj3p+GPy0C9qBAnTjim14oME4D07bRmSZAVLA9vekHz5prpdHREtHflixHBHSo7uRp4+dpqO0jWMBbcFR0JAyaynIyfLGBgY6Vlc36dmPm+0i5JzgY5+aDqaoZ1Kj1BcH5p22ZWs1YY5UUhhpLkljyOlec9Ei1sxUtt9XUVT3KvM5HlMCfSQ3BFdhLCYbc79pyP61zc8Ts7suWYH880lSkZCsMaqqlQOoNPabMrKWVsbTyaUu0RY8E5kIyc9BQbHgyEHG0ZA96A6galgh2YK20DAOcihrdEzRRnP7w8A9hVHHcJ95bIb+UdiCKcllbfFvkUnacN7UYS8uJEkUHbkgekD3rUEsLWpmmUI4w4OcYwarTekxoqEnb1ZehNZeasDZtAqhQUwARkn4+lB6vbG/N3LI5BMZ2gDsferCPNrO7E+xBx3rkNPuUtPu4LHcCCeoB+M+9dUbqOVMb8luQRyKRGzL96YMnqb2FPKUih3N+If1qitBIl194j6FxuTsadvLvzSgQlCOSD1FOGgPOlvXaMBYi2PUefyFW3nTLBtZV54BFKaYgZRIXBznA+aya5XzigfKqKXyF9CgctfPEcg8dutWM9yYLZg0Zc52470lE+8livqBySa3JMZJt8nOPTx0FHz4Zq1T94CjFlPqZT2PxRXk3SK+5sZ70sCkCmWOUZYYBz7dqDFdPNGweLYQ2BjvSOLuEqygjg+/eps+V27w3txVbFM7cZHp4IPFHe7AwEUs/K8HpikDEWdg5PPUGpzyLHBkAbgRgA9Oarmll5Jn8tTjhecmtSFZQqmeQgnClsA5oB6W5WWRgpJC9gOh9qVmmeCY+UMSSLjeegwe9LTqyQhYG9XTdj+tJztdqN4ERETZLbyBjuCPmkZ61cO/77CSgkEvz+dHjljWZREDw23dt74qnlnMsqebG5PDBBgnmp22pH7wIGiZUDEhpfTj4+TQFzua3eXK7wwXOe5NPNcpKQEDAgbfUOgPaqe3Z/vm1mOCASx44GfenjdkWuCCTGNwYDhqc+Es4MI83lAEA42+3FCkYShiw29cZOKVV5YneSL1Buu3nj3ocVzHIgmlG9h1GOAO2P6UEeHmMNgKO2Bndxilp4/Kt2Jl2ykdhnn/AGo6uWHpxgH1MPwijxqoVi2C3TcDQbmNPjhnM6uVMickEZNL3Wh2f3sTRQ+XI3Vk7/lV1JbJJdtJsAcDAI4yOnNJXUEsZdwSD0X3NJW65W60iR726KSII5EKbccjHSo6Et7bWciXFuY3RvxHvVlctLDOJGG7j1Z70X74pPIVk+KW+sVJl0e0vpC4IYEjtVwbCx1+0kstSgjuIHGTG4yM+/wfpVGfL3LJGQo+OasLRCJY3SUMoP4hRxcq+7LHj3jT7NNR8N3kt1YRy3Ongll43Mq/5xVh4C1ue4tzpz3ssRj5TADAj256Yr2e8v5YtPYRx+ZIcKAFzjPfFef6l4GGqXb6vokIsdQh5Kldi3Hvx0B+a7ue5frzbzd9LiDQ7gs0suqzBD+BFAXA+aej0ON1BlvLmQ46F+KBbytqFmsUwktblDtljcepT/8AOhpi3vYbB/Kcse2WOc1qzxOPRYIiDDCBjqTzR47O2j9TDcR+lPwTpNDuU5BFJTmOAlpDkk8D3NPSwQzxqhPpVR+Qqskvpr19lr6YxwZT0J+PeiPEJ2/fn92f+32P1pK6vvNk8mEKEXjijTwQSFMxo7O44JNNQBguWPPekIY9hznn3NMrOEyDyKX007knOQeKUMzjjNaluOozSclwQKCMGVyeTUlJxSkcwc5Jos1wkURLECqJuW6SLjq3tSRlMsmTyewoSxS302Y1Yr/MelXFjYRW+CfU3uaZC6fprOweXhfai6vo4ubYPbnZPD6l+firCFhtGO1EdvRRCxz9zcahD4f86JI98YDMGPOPpU7dje2aSEAMRyAaNq93BBZeW4LGf0KoOMk1CxWGxs1jLZIHNP8AhT1VVPCyTtgHFSt1AQljj2o99exjoV5qmmvHmYRxn61K90W7ndiI4mJAOSRXTaZciS3iZlCyLgkVy4326lxgt2qy0W5LO25+vWqlTYc13TkE/wB+gUBXO5gPfuaSVweO9dBE/nQvCQG28gHv71z91B93uDt/A3Kn4q+brKxhNSiPPWhAljgU1Gi4BarZ0/Zo+zccbatIpVxgDNU0chBA7DpVhayBnA704hcRMcD3pyIlhzxSkA45ptOBWkQbQKEzmhNNiXGaFvIBOcUKJt0hNNK3imUpW2JIJWko5AKbSTI4oJBlzQygo5BYHigyEIuTQReQhc0soM0p54qM0xeTaD1pq2jxjtQYsQxxUyVHJ/SoGBs534oZgUZLMxx05oCa/vJQgXknjNdNo5OHDTBinpCjoKo9GRPN3ue2FJ966a2RBK2yNVJxkgYrn8l/jr8PPrT235NZUPLY9xWVz43x8zQXKrb7QxUEdCenxQ7WaOS4YdCOgPU1X/eonkkRGHokyMnqKas/LmMkoYI5Y988VxO9a3HqUK3TqRVJGN37xVywJGex5pma4Z2dWIAXA56mo3kghtEiZVUEZYnqP0pKUurweoEHJPO1exqslklSyJUEsmDn4zzTl8js8UrZ/eccdfrW7qKJbLY4k2Hp2Jx2pwE4L2KS4g8wGPc3B65HvTl4VZUnQ8Jn055NU22N7xDAxRY+QGOce9EuJSHViMHOCQeAKZOk0q4SYKGwqnqanqDxi6gLyBgnQKOwzwfmqezvIoFCsCQTkEe1O3FwjbWiXzc9B0zQS/0yKOSGfzAcPjaCfigTIbRlWGZo3PJAbikbW5nRVM6RgoccHjFNW93wWMJlDN6sKSaQN2+oy21syy4dc5yeCKOmoxXsyqoZZChLgjoe1Uupm8ECSBESOVssGbkfGPyqOjahaSTIGkEeAR6zgfnSN11nhbL1yMY1UsVPc0st2DKp8oOnTPTH51TXd+hixHMignLAnHFSt7szRO/ltjG4Be2KMDqfveyJAUCFgMd9xpSzJlCh1yd5zjjFKPqSzsP4wFww6EfNTsrsQTl85jYAE45z/wDBQcXM0ivwIsFBwV70CCY7ZFO8DOcnsaSbUQVJ3ck9uKLFOtxGfMYbgMYHQ1KsWsEiSRZeVf8AyHU0zCVjKqAD89jVQjxxHy/MVFxkg8Y+RTEEqtJkOGHUk8ZpA+ylIZDgbWHpGOlLzHzGVAei5IIrb3ZCrnJ2ex6Uvd3O2RpEXfuQbgvPvimBfOW1w0hO1ec4Jx+lAjLT20m5sox3gAf3qDSsbEbvUQMk9fyoXmF9PZ4TsmAOQO2KQPQyJzEq7soQG+c8VMwo1q3mAv0DA9qrI5x92jIfGPUW3Uwly6SgMu6OQc8nt05owk3mCKIpxtwBtYck/r1qwjmfyliufMLnuvGR9Kq7FGnvIpZ4/wB2Pwgc4/8AdVleXwSFTtcshO7jrz1FMhIrwR7lVz5XcnPpxxSkd9tXAXzFYHt0AJwajHKbsOX/AHavJyT1xj2rN6W12rDaFhTAA4LfBFI1nZamjREsdo6btpGB8inDPAW3xqzDgelSMiqJjGs7E5aNjgFQcZxRbeb7yjOrsedu1WOBSNa226XzGd3CIeeOnsKYkg9IZ/WSMZHBFIWRSR/3bleSSAeGxxVsjhogTljjIzTDmdRs9pQnBJyc1SPCnqG04B4xxXZ3kUby7iy5252Hqef71z2pQSJIWKbUYdep/wCKixXNUQZ7e44bII6e1WFnfiCUjGM88UnJbnzCQDjGRnvQBmN8gmlPS812NpqUUrbi461Zr+8IdHwfeuGinyoI47VZWWqSQsBvIqv3/tP4z46q4t4rzY08JWdBhZk9vY+4rlta0xFzJc3P3fHIYDg10FjrCvgPgE98dasvLhuo+gOeeQDXT4/I5++JXC6dqUltbGKz8y6K/wAbLtWn4I5y3nXkplmI49kHsB/mntU0+SzkacjKdjjgVVGWW8cxRypEh/FIRk/QV0bK5/zYFfXhZzbRHJHLkHp8VCAKijA5pttLitrfKuXbux70kvDYpkMWyaGXxk5rGwueaDkynCHI7mqhVmWkfaKBegRYFMtMlvFgct3NVbQ3Os3flW/pQfjk7KP96ZILd4fanrc/hUDJJp+20l7iQTX757iJen505b6Zb6XEdgzIernqagLwh8YyKAsgiKm0DaB0ArFXHIpRbgHk1pr3ZkDpTStbdwrc9KPI8ezrj865175uucUnPq2wHLE+1AP67Cl9YPCrKHBDKfkf2rmPvupmKSEssUiHG7O7J+KtoLTVNUH7uMwxH+N+KsovCKxwtmdmmKnDY4zThY89tk12XXY4LgyXEB/j24H1+K9CtdIgt4wSoLd+KS0tbuwsmt3smZoicuWADH61vQNcOoRSxToqyRseAe1K+hKPqESANwOntVVbv5V0COh9qtb59+7A7VT7CpLGs9aZ6dZaygIkgHShXtoJTLGvH8cY9s0nps5mhEWcD3qznXNmsv8A3ITgkdxV81nYoI3WL8fDVNLjc3PSo61ZmOYXKEmOXnHsaDbcjFbsbFnG+RVlpxBcsOcVSq5Aq50j1IW+abOr2NzxxR0cnvilkfipeb7VcZ0a4fbHgd6y2BPTn5pW4fAHXmjRTEIApwKpKzSFV560QOE6UikjsKIA+OtMjgnLLycUrdy5GK1tbB5pN5dzkUE3DH6i3erCIcUrbr6cnrRxwOtAHz7mhs6E7ScseB80FnOQo5Jq90jSGjPnzqCwHC4zipvWRXHN6qelafIIt0kTIytwD0Za6GNFVQcAcfkKjEu0Yx88UQsAu7qMdq4+rr0JMmNeaB2rKr5dchilZCME
