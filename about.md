---
title: Ryder McDowell
permalink: /about/
layout: page
excerpt: Hello peeps, I'm student of computer science from Banyuwangi, living in Jogjakarta. This blog for documentation about my programming journey, running on jekyll, hosting on netlify and using my own simple theme.
comments: false
---

Hello, I'm Ryder, and I'm in my third year at UChicago studying mathematics and physics. Broadly, I'm interested in condensed matter theory, and most recently I've been working with QCAs (Quantum Cellular Automata), boundary algebras, and generalized symmetries. This summer, I'll be at UMD working on an AQFT (Algebraic Quantum Field Theory) project. In addition to research, I have extensive experience in STEM outreach. Being from a low-income, underserved background myself, I'm especially interested in opportunities that connect underrepresented youth with high-quality STEM experiences.

<div class="carousel" id="carousel-0">
  <div class="carousel-window">
    <div class="carousel-track" id="track-0">
      <img src="/assets/img/florida_2.jpg" alt="Photo 1">
      <img src="/assets/img/fl_1.png" alt="Photo 2">
      <img src="/assets/img/fl_2.JPG" alt="Photo 3">
      <img src="/assets/img/fl_3.JPG" alt="Photo 4">
      <img src="/assets/img/fl_4.JPG" alt="Photo 5">
      <img src="/assets/img/fl_5.JPG" alt="Photo 6">
      <img src="/assets/img/fl_6.JPG" alt="Photo 7">
      <img src="/assets/img/fl_7.JPG" alt="Photo 8">
    </div>
  </div>
  <button class="carousel-btn prev" onclick="moveCarousel(0, -1)">&#8592;</button>
  <button class="carousel-btn next" onclick="moveCarousel(0, 1)">&#8594;</button>
</div>

Outside of school, I play the guitar, paint, and do a lot of biking when I get the chance.

<div class="carousel" id="carousel-1">
  <div class="carousel-window">
    <div class="carousel-track" id="track-1">
      <img src="/assets/img/art_1.jpeg" alt="Photo 1">
      <img src="/assets/img/art_2.jpeg" alt="Photo 2">
      <img src="/assets/img/art_3.jpeg" alt="Photo 3">
      <img src="/assets/img/art_4.jpeg" alt="Photo 4">
      <img src="/assets/img/art_5.jpeg" alt="Photo 5">
      <img src="/assets/img/art_6.jpeg" alt="Photo 6">
    </div>
  </div>
  <button class="carousel-btn prev" onclick="moveCarousel(1, -1)">&#8592;</button>
  <button class="carousel-btn next" onclick="moveCarousel(1, 1)">&#8594;</button>
</div>

<style>
.carousel {
  position: relative;
  width: 100%;
  max-width: 500px;
  margin: 1.2rem auto;
}
.carousel-window {
  overflow: hidden;
  width: 100%;
  border-radius: 8px;
  background: #131418;
}
.carousel-track {
  display: flex;
  transition: transform 0.4s ease;
  will-change: transform;
}
.carousel-track img {
  flex: 0 0 100%;
  width: 100%;
  object-fit: cover;
  height: 340px;
}
#carousel-1 .carousel-track img {
  object-fit: contain;
  height: 480px;
  background: #131418;
}
#carousel-0 .carousel-track img:nth-child(3) {
  object-fit: contain;
  background: #131418;
}
.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0,0,0,0.4);
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  cursor: pointer;
  font-size: 1.5rem;
  border-radius: 4px;
  z-index: 10;
}
.prev { left: 8px; }
.next { right: 8px; }
</style>

<script>
const positions = {};
function moveCarousel(id, dir) {
  const track = document.getElementById(`track-${id}`);
  const total = track.children.length;
  if (positions[id] === undefined) positions[id] = 0;
  positions[id] = (positions[id] + dir + total) % total;
  track.style.transform = `translateX(-${positions[id] * 100}%)`;
}
</script>

Email me at: mcdowellr [at] uchicago [dot] edu