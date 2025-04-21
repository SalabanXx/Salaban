<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Salaban. | Portfolio</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background: #0f0f0f;
      color: #fff;
      line-height: 1.6;
    }

    header {
      background: #111;
      padding: 1.5rem 0;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .container {
      width: 90%;
      max-width: 1200px;
      margin: auto;
    }

    header .container {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    nav a {
      color: #fff;
      margin-left: 2rem;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.3s;
    }

    nav a:hover {
      color: #00f7ff;
    }

    .hero {
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
      background: linear-gradient(to right, #1f1c2c, #928dab);
      animation: fadeIn 2s ease forwards;
      position: relative;
    }

    .hero h1 {
      font-size: 3rem;
      font-weight: 700;
      animation: blurFadeIn 3s ease-in-out forwards;
    }

    .hero p {
      font-size: 1.2rem;
      margin-top: 1rem;
      color: #eee;
      animation: fadeInUp 2s 1s ease forwards;
      opacity: 0;
    }

    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(30px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeInUp {
      0% { opacity: 0; transform: translateY(20px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    @keyframes blurFadeIn {
      0% {
        filter: blur(10px);
        opacity: 0;
        transform: scale(1.1);
      }
      100% {
        filter: blur(0);
        opacity: 1;
        transform: scale(1);
      }
    }

    .profile-section {
      text-align: center;
      margin-top: 4rem;
      animation: fadeInUp 1.5s ease-in-out forwards;
    }

    .profile-pic {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      object-fit: cover;
      border: 3px solid #00f7ff;
      margin-bottom: 1rem;
    }

    .portfolio {
      padding: 5rem 0;
      background: #181818;
      text-align: center;
      opacity: 0;
      transform: translateY(50px);
      transition: opacity 1s ease, transform 1s ease;
    }

    .portfolio.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .portfolio h2 {
      font-size: 2.5rem;
      margin-bottom: 3rem;
    }

    .portfolio-gallery {
      display: flex;
      flex-wrap: wrap;
      gap: 2rem;
      justify-content: center;
    }

    .portfolio-slide {
      width: calc(30% - 2rem);
      position: relative;
      cursor: pointer;
      min-width: 300px;
    }

    .video-wrapper {
      position: relative;
      width: 100%;
      padding-top: 56.25%;
      overflow: hidden;
      border-radius: 12px;
    }

    .video-wrapper video {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      filter: grayscale(0.4) brightness(0.8);
      transition: filter 0.3s ease;
      pointer-events: none;
    }

    .portfolio-slide:hover video {
      filter: grayscale(0) brightness(1);
    }

    .overlay {
      position: absolute;
      bottom: 10px;
      left: 10px;
      background: rgba(0, 0, 0, 0.6);
      padding: 0.5rem 1rem;
      border-radius: 6px;
      opacity: 0;
      transform: translateY(10px);
      transition: opacity 0.5s ease, transform 0.5s ease;
    }

    .portfolio-slide:hover .overlay {
      opacity: 1;
      transform: translateY(0);
    }

    .overlay h3 {
      color: #00f7ff;
      font-size: 0.85rem;
      margin: 0;
    }

    .about {
      padding: 5rem 0;
      background: #121212;
      text-align: center;
    }

    .about h2 {
      font-size: 2.5rem;
      margin-bottom: 2rem;
      animation: fadeInUp 2s ease forwards;
    }

    .about p {
      max-width: 600px;
      margin: auto;
      font-size: 1.1rem;
      color: #ccc;
      animation: fadeIn 2s 1s ease forwards;
      opacity: 0;
    }

    footer {
      background: #0d0d0d;
      text-align: center;
      padding: 2rem 0;
      font-size: 0.9rem;
      color: #666;
    }
  </style>
  <script>
    window.addEventListener('DOMContentLoaded', () => {
      const observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            observer.unobserve(entry.target);
          }
        });
      }, { threshold: 0.3 });

      const portfolioSection = document.querySelector('.portfolio');
      observer.observe(portfolioSection);

      const slides = document.querySelectorAll('.portfolio-slide');
      slides.forEach(slide => {
        const video = slide.querySelector('video');
        video.muted = false;
        video.loop = true;

        slide.addEventListener('click', () => {
          slides.forEach(other => {
            const otherVideo = other.querySelector('video');
            if (other !== slide) otherVideo.pause();
          });

          if (video.paused) video.play();
          else video.pause();
        });
      });
    });
  </script>
</head>
<body>
  <header>
    <div class="container">
      <h1>Salaban.</h1>
      <nav>
        <a href="#portfolio">Portfolio</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
      </nav>
    </div>
  </header>

  <section class="hero">
    <div class="container">
      <h1>Hello, I'm Salaban.</h1>
      <p>I'm a Video Editor and VFX Artist with a passion for clean, functional design and impactful storytelling. I bring ideas to life through sharp visuals, seamless edits, and creative problem-solving—blending technical precision with a strong design sensibility.</p>
    </div>
  </section>

 

  <section id="portfolio" class="portfolio">
    <div class="container">
      <h2>Portfolio</h2>
        <div class="portfolio-gallery">
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077180212?h=9a1b2dcff7" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>My Eyes Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077184498?h=609f8c7598" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Real Demon Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179594?h=26be676450" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>A$ap Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179657?h=bce3840e6f" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Kendrick Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179905?h=4bbc101370" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Hits From the Bong Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179924?h=b52f50e7ca" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Insane Brain Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077180270?h=9115444e2d" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Unfair Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077180020?h=5e8b2dc683" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Lost Forever Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179840?h=110253600b" width="640" height="360" frameborder="0"    allowfullscreenS style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Eusexua Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179951?h=057b2dc7fe" width="640" height="360" frameborder="0"    allowfullscreen  style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>LDR Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077180164?h=980b4cf2ab" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>M'$ Project</h3></div>
          </div>
          <div class="portfolio-slide">
            <div class="video-wrapper">
              <iframe title="vimeo-player" src="https://player.vimeo.com/video/1077179867?h=f84fc80049" width="640" height="360" frameborder="0"    allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
            </div>
            <div class="overlay"><h3>Ghost Town Project</h3></div>
          </div>
        </div>
        
  </section>

  <section id="about" class="about">
    <div class="container">
      <h2>About Me</h2>
      <p>I’m a Video Editor and VFX Artist with a creative mind and a passion for turning ideas into eye-catching visuals. I use tools like Blender, After Effects, DaVinci Resolve, Photoshop, and Illustrator to bring my concepts to life through smooth edits, unique effects, and strong visual storytelling.

        I work with anime scenes, real footage, or just images—whatever fits the vision. For me, editing is more than just cutting clips together. It’s where my third eye opens. It’s how I see beyond the surface and create something that captures attention and communicates a clear message.
        
        I’m not taking things too seriously just yet. I’m still exploring, learning, and having fun with every project. But I always bring creativity, focus, and detail to everything I make.
        
        Let’s see where this creative journey goes.</p>
    </div>
  </section>

  <footer id="contact">
    <div class="container">
      <p>Contact me at <a href="mailto:badrelghaly@gmail.com" style="color:#00f7ff;text-decoration:none;">badrelghaly@gmail.com</a> | Follow me <a href="https://www.instagram.com/salabvn/" target="_blank" style="color:#00f7ff;text-decoration:none;">@Salabvn</a> </a><a href="https://www.instagram.com/salaban.again/" target="_blank" style="color:#00f7ff;text-decoration:none;">@Salaban.again</a></p>
    </div>
  </footer>
</body>
</html>
