f<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday</title>  <!-- Tailwind CSS -->  <script src="https://cdn.tailwindcss.com"></script>  <!-- GSAP -->  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>  <!-- Font Awesome -->  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />  <!-- Google Fonts -->  <link href="https://fonts.googleapis.com/css2?family=Pacifico&family=Playfair+Display:wght@400;600&display=swap" rel="stylesheet">  <style>
    body { font-family: 'Playfair Display', serif; }
    .pacifico { font-family: 'Pacifico', cursive; }
    .blur-in { filter: blur(20px); }
  </style></head>
<body class="bg-black text-white overflow-hidden"><!-- Background hearts --><div id="hearts" class="fixed inset-0 -z-10"></div><!-- Music --><audio id="bgMusic" loop>
  <source src="music.mp3" type="audio/mpeg">
</audio><!-- Envelope Screen --><section id="envelopeScreen" class="h-screen flex items-center justify-center">
  <div id="envelope" class="cursor-pointer text-center">
    <i class="fa-solid fa-envelope text-7xl text-pink-400"></i>
    <p class="pacifico text-3xl mt-4">Click to Open</p>
  </div>
</section><!-- Main Content --><section id="main" class="hidden min-h-screen flex flex-col items-center justify-center px-6">  <!-- Image 1 -->  <img id="img1" src="her1.jpg" class="w-72 rounded-2xl blur-in" />  <!-- Birthday Text -->  <div id="text1" class="opacity-0 mt-10 text-center whitespace-pre-line leading-relaxed">
✦✧✦✧✦✧✦✧✦✧✦✧✦✧✦  
🌟💛 Happy Birthday 💛🌟  
✦✧✦✧✦✧✦✧✦✧✦✧✦✧✦✨
"Teri humse mulaaqat ne zindagi ko rangin bana diya..." ✨

💎 Allah tumhein hamesha shadab rakhe 💎

  </div>
<!-- Image 2 -->  <img id="img2" src="her2.jpg" class="w-72 rounded-2xl blur-in mt-12 hidden" />  <!-- Final Text -->  <h1 id="finalText" class="pacifico text-4xl mt-16 opacity-0">Stay Blessed and Live a Long Life</h1>
  <p id="finalName" class="pacifico text-2xl mt-2 opacity-0">Adelica</p>
</section><script>
// Floating hearts
for (let i = 0; i < 30; i++) {
  const heart = document.createElement('div');
  heart.innerHTML = '💖';
  heart.style.position = 'absolute';
  heart.style.left = Math.random() * 100 + '%';
  heart.style.top = Math.random() * 100 + '%';
  heart.style.fontSize = Math.random() * 24 + 16 + 'px';
  heart.style.opacity = 0.6;
  document.getElementById('hearts').appendChild(heart);
  gsap.to(heart, { y: -100, duration: 6 + Math.random() * 6, repeat: -1, yoyo: true });
}

// Envelope click
document.getElementById('envelope').addEventListener('click', () => {
  document.getElementById('bgMusic').play();
  gsap.to('#envelopeScreen', { opacity: 0, duration: 1, onComplete: () => {
    document.getElementById('envelopeScreen').classList.add('hidden');
    document.getElementById('main').classList.remove('hidden');

    // Image 1 blur animation
    gsap.to('#her1', { filter: 'blur(0px)', duration: 2 });

    // Text
    gsap.to('#text1', { opacity: 1, delay: 2, duration: 2 });

    // Image 2
    gsap.to('#her2', { delay: 6, onStart: () => {
      document.getElementById('img2').classList.remove('hidden');
      gsap.to('#her2', { filter: 'blur(0px)', duration: 2 });
    }});

    // Final text
    gsap.to('#finalText', { opacity: 1, delay: 9, duration: 2 });
    gsap.to('#finalName', { opacity: 1, delay: 10, duration: 2 });
  }});
});
</script></body>
</html>
