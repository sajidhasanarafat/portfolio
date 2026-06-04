
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Arafat Sajid — Drone Videographer</title>
  <link
    href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&family=Space+Mono:wght@400;700&display=swap"
    rel="stylesheet">
  <style>
    *,
    *::before,
    *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0
    }

    :root {
      --sky: #0a0e1a;
      --sky2: #0d1220;
      --sky3: #111827;
      --gold: #e8c96d;
      --gold2: #f5dfa0;
      --sky-blue: #5b9bd5;
      --horizon: #ff7e45;
      --text: #e8eaf0;
      --muted: #7a8499;
      --border: rgba(232, 201, 109, 0.12);
      --card: rgba(17, 24, 39, 0.85);
      --glow: rgba(232, 201, 109, 0.15);
    }

    html {
      scroll-behavior: smooth
    }

    body {
      background: var(--sky);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-size: 16px;
      line-height: 1.6;
      overflow-x: hidden;
      min-height: 100vh;
    }

    /* ── NOISE TEXTURE ── */
    body::after {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 999;
      opacity: 0.45;
    }

    /* ── STAR FIELD ── */
    .stars {
      position: fixed;
      inset: 0;
      pointer-events: none;
      overflow: hidden;
      z-index: 0
    }

    .stars span {
      position: absolute;
      border-radius: 50%;
      background: white;
      opacity: 0;
      animation: twinkle var(--d) ease-in-out infinite var(--delay);
    }

    @keyframes twinkle {

      0%,
      100% {
        opacity: 0
      }

      50% {
        opacity: var(--op)
      }
    }

    /* ── SCROLLBAR ── */
    ::-webkit-scrollbar {
      width: 4px
    }

    ::-webkit-scrollbar-track {
      background: var(--sky)
    }

    ::-webkit-scrollbar-thumb {
      background: var(--gold);
      border-radius: 2px
    }

    /* ── NAV ── */
    #nav {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 100;
      padding: 1.2rem 2rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: rgba(10, 14, 26, 0.6);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      transition: all 0.3s;
    }

    #nav.scrolled {
      background: rgba(10, 14, 26, 0.95);
      padding: 0.9rem 2rem
    }

    .nav-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.6rem;
      letter-spacing: 0.08em;
      color: var(--gold);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .nav-logo .drone-icon {
      width: 28px;
      height: 28px;
      background: linear-gradient(135deg, var(--gold), var(--horizon));
      border-radius: 6px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.9rem;
      animation: hover-drone 3s ease-in-out infinite;
    }

    @keyframes hover-drone {

      0%,
      100% {
        transform: translateY(0)
      }

      50% {
        transform: translateY(-4px)
      }
    }

    .nav-links {
      display: flex;
      align-items: center;
      gap: 2.5rem;
      list-style: none
    }

    .nav-links a {
      color: var(--muted);
      font-size: 0.88rem;
      font-weight: 500;
      text-decoration: none;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      transition: color 0.2s;
      position: relative;
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -4px;
      left: 0;
      right: 0;
      height: 1px;
      background: var(--gold);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.25s;
    }

    .nav-links a:hover {
      color: var(--gold2)
    }

    .nav-links a:hover::after {
      transform: scaleX(1)
    }

    .btn-hire {
      padding: 0.5rem 1.3rem;
      background: linear-gradient(135deg, var(--gold), var(--horizon));
      color: #0a0e1a;
      font-weight: 700;
      font-size: 0.82rem;
      border-radius: 50px;
      text-decoration: none;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      transition: opacity 0.2s, transform 0.2s;
      white-space: nowrap;
    }

    .btn-hire:hover {
      opacity: 0.88;
      transform: translateY(-1px)
    }

    /* HAMBURGER */
    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
      background: none;
      border: none;
      padding: 4px;
      outline: none;
      -webkit-tap-highlight-color: transparent;
    }

    .hamburger span {
      display: block;
      width: 24px;
      height: 2px;
      background: var(--text);
      border-radius: 2px;
      transition: transform 0.3s ease, opacity 0.2s ease;
    }

    .hamburger.open span:nth-child(1) {
      transform: translateY(7px) rotate(45deg)
    }

    .hamburger.open span:nth-child(2) {
      opacity: 0
    }

    .hamburger.open span:nth-child(3) {
      transform: translateY(-7px) rotate(-45deg)
    }

    /* MOBILE DRAWER */
    .drawer {
      position: fixed;
      top: 0;
      right: 0;
      left: auto;
      bottom: 0;
      width: 75%;
      max-width: 280px;
      background: rgba(10, 14, 26, 0.85);
      border-left: 1px solid var(--border);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      z-index: 200;
      transform: translateX(100%);
      visibility: hidden;
      transition: transform 0.32s cubic-bezier(.4, 0, .2, 1), visibility 0.32s;
      display: flex;
      flex-direction: column;
      gap: 0;
      padding: 5rem 2rem 2rem;
    }

    .drawer.open {
      transform: translateX(0);
      visibility: visible;
    }

    .drawer a:not(.btn-hire) {
      color: var(--text);
      font-size: 1.1rem;
      font-weight: 500;
      text-decoration: none;
      padding: 0.9rem 0;
      border-bottom: 1px solid var(--border);
      transition: color 0.2s, padding-left 0.2s;
    }

    .drawer a:not(.btn-hire):hover {
      color: var(--gold);
      padding-left: 0.5rem;
    }

    .drawer .btn-hire {
      margin-top: 2rem;
      text-align: center;
      display: block;
      color: #0a0e1a;
    }

    .overlay {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.6);
      z-index: 190;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .overlay.show {
      opacity: 1;
      pointer-events: all
    }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 6rem 1.5rem 4rem;
      position: relative;
      overflow: hidden;
    }

    /* Sky gradient background */
    .hero-bg {
      position: absolute;
      inset: 0;
      background:
        radial-gradient(ellipse 80% 50% at 50% 110%, rgba(255, 126, 69, 0.18) 0%, transparent 60%),
        radial-gradient(ellipse 60% 40% at 20% 80%, rgba(91, 155, 213, 0.12) 0%, transparent 60%),
        radial-gradient(ellipse 50% 30% at 80% 90%, rgba(232, 201, 109, 0.08) 0%, transparent 60%),
        var(--sky);
      z-index: -1;
    }

    /* Horizon line */
    .horizon-line {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--gold), var(--horizon), var(--sky-blue), transparent);
      opacity: 0.4;
    }

    .hero-eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      padding: 0.4rem 1rem;
      border: 1px solid var(--border);
      border-radius: 50px;
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      color: var(--gold);
      letter-spacing: 0.1em;
      text-transform: uppercase;
      margin-bottom: 2rem;
      background: rgba(232, 201, 109, 0.06);
      animation: fade-up 0.8s ease both;
    }

    .hero-eyebrow .dot {
      width: 6px;
      height: 6px;
      border-radius: 50%;
      background: var(--horizon);
      animation: pulse 2s ease infinite;
    }

    @keyframes pulse {

      0%,
      100% {
        box-shadow: 0 0 0 0 rgba(255, 126, 69, 0.7)
      }

      50% {
        box-shadow: 0 0 0 6px rgba(255, 126, 69, 0)
      }
    }

    .hero h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(4rem, 14vw, 11rem);
      line-height: 0.9;
      letter-spacing: 0.03em;
      color: var(--text);
      animation: fade-up 0.8s ease 0.1s both;
    }

    .hero h1 .gold {
      color: transparent;
      -webkit-text-stroke: 2px var(--gold);
    }

    .hero h1 .block {
      display: block
    }

    .hero-sub {
      font-size: clamp(1rem, 2.5vw, 1.25rem);
      color: var(--muted);
      font-weight: 300;
      max-width: 560px;
      margin: 1.5rem auto 2.5rem;
      animation: fade-up 0.8s ease 0.2s both;
    }

    .hero-sub strong {
      color: var(--gold2);
      font-weight: 500
    }

    .hero-cta {
      display: flex;
      align-items: center;
      gap: 1rem;
      flex-wrap: wrap;
      justify-content: center;
      animation: fade-up 0.8s ease 0.3s both;
    }

    .btn-primary {
      padding: 0.85rem 2rem;
      background: linear-gradient(135deg, var(--gold), var(--horizon));
      color: #0a0e1a;
      font-weight: 700;
      font-size: 0.9rem;
      border-radius: 50px;
      text-decoration: none;
      letter-spacing: 0.04em;
      transition: transform 0.2s, box-shadow 0.2s;
      box-shadow: 0 4px 24px rgba(232, 201, 109, 0.25);
    }

    .btn-primary:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 32px rgba(232, 201, 109, 0.35)
    }

    .btn-outline {
      padding: 0.85rem 2rem;
      border: 1px solid var(--border);
      color: var(--text);
      font-weight: 500;
      font-size: 0.9rem;
      border-radius: 50px;
      text-decoration: none;
      letter-spacing: 0.04em;
      transition: border-color 0.2s, background 0.2s;
    }

    .btn-outline:hover {
      border-color: var(--gold);
      background: rgba(232, 201, 109, 0.06)
    }

    /* Floating altitude badge */
    .altitude-badge {
      position: absolute;
      right: 5%;
      top: 30%;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 0.8rem 1.2rem;
      backdrop-filter: blur(12px);
      animation: float 4s ease-in-out infinite;
      display: flex;
      flex-direction: column;
      gap: 0.2rem;
    }

    .altitude-badge .val {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 1.8rem;
      color: var(--gold);
      line-height: 1;
    }

    .altitude-badge .lbl {
      font-size: 0.7rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    /* Coords badge */
    .coords-badge {
      position: absolute;
      left: 3%;
      bottom: 25%;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 0.7rem 1.1rem;
      backdrop-filter: blur(12px);
      animation: float 5s ease-in-out infinite reverse;
      font-family: 'Space Mono', monospace;
      font-size: 0.72rem;
      color: var(--sky-blue);
    }

    @keyframes float {

      0%,
      100% {
        transform: translateY(0)
      }

      50% {
        transform: translateY(-10px)
      }
    }

    @keyframes fade-up {
      from {
        opacity: 0;
        transform: translateY(24px)
      }

      to {
        opacity: 1;
        transform: translateY(0)
      }
    }

    /* ── SCROLL INDICATOR ── */
    .scroll-hint {
      position: absolute;
      bottom: 2.5rem;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.5rem;
      color: var(--muted);
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
    }

    .scroll-arrow {
      width: 24px;
      height: 38px;
      border: 1.5px solid rgba(232, 201, 109, 0.3);
      border-radius: 12px;
      position: relative;
      overflow: hidden;
    }

    .scroll-arrow::after {
      content: '';
      position: absolute;
      top: 6px;
      left: 50%;
      transform: translateX(-50%);
      width: 4px;
      height: 4px;
      border-radius: 50%;
      background: var(--gold);
      animation: scroll-dot 2s ease infinite;
    }

    @keyframes scroll-dot {
      0% {
        transform: translate(-50%, 0);
        opacity: 1
      }

      100% {
        transform: translate(-50%, 18px);
        opacity: 0
      }
    }

    /* ── SECTIONS COMMON ── */
    section {
      padding: 6rem 1.5rem;
      position: relative;
      z-index: 1
    }

    .container {
      max-width: 1140px;
      margin: 0 auto
    }

    .section-tag {
      font-family: 'Space Mono', monospace;
      font-size: 0.72rem;
      color: var(--gold);
      letter-spacing: 0.15em;
      text-transform: uppercase;
      margin-bottom: 0.8rem;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .section-tag::before,
    .section-tag::after {
      content: '';
      width: 24px;
      height: 1px;
      background: var(--gold);
    }

    .section-title {
      font-family: 'Bebas Neue', sans-serif;
      font-size: clamp(2.5rem, 6vw, 4.5rem);
      letter-spacing: 0.04em;
      line-height: 1;
      margin-bottom: 1rem;
      text-align: center;
    }

    /* ── ABOUT ── */
    #about {
      background: var(--sky2)
    }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: center;
      margin-top: 3rem;
    }

    .about-text p {
      color: var(--muted);
      line-height: 1.8;
      margin-bottom: 1.2rem;
      font-size: 1.02rem;
    }

    .about-text p strong {
      color: var(--text)
    }

    .skills-list {
      margin-top: 2rem;
      display: flex;
      flex-direction: column;
      gap: 1.2rem
    }

    .skill-row {}

    .skill-top {
      display: flex;
      justify-content: space-between;
      font-size: 0.85rem;
      margin-bottom: 6px;
      font-weight: 500;
    }

    .skill-top span:last-child {
      color: var(--gold);
      font-family: 'Space Mono', monospace
    }

    .skill-track {
      height: 5px;
      background: var(--border);
      border-radius: 5px;
      overflow: hidden
    }

    .skill-fill {
      height: 100%;
      background: linear-gradient(90deg, var(--gold), var(--horizon));
      border-radius: 5px;
      width: 0;
      transition: width 1.2s cubic-bezier(.4, 0, .2, 1);
    }

    .stats-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1rem;
      margin-top: 2.5rem;
    }

    .stat-box {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 1.2rem 1rem;
      text-align: center;
      transition: border-color 0.2s, transform 0.2s;
    }

    .stat-box:hover {
      border-color: var(--gold);
      transform: translateY(-3px)
    }

    .stat-num {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.2rem;
      color: var(--gold);
      line-height: 1;
    }

    .stat-lbl {
      font-size: 0.78rem;
      color: var(--muted);
      margin-top: 0.3rem
    }

    /* Floating drone visual */
    .drone-visual {
      position: relative;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .drone-circle {
      width: 320px;
      height: 320px;
      border-radius: 50%;
      background: radial-gradient(circle at 40% 35%, rgba(232, 201, 109, 0.08), transparent 70%),
        radial-gradient(circle at 60% 65%, rgba(255, 126, 69, 0.06), transparent 70%);
      border: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      animation: float 5s ease-in-out infinite;
    }

    .drone-circle::before {
      content: '';
      position: absolute;
      inset: -20px;
      border-radius: 50%;
      border: 1px dashed rgba(232, 201, 109, 0.1);
      animation: spin 20s linear infinite;
    }

    .drone-circle::after {
      content: '';
      position: absolute;
      inset: -40px;
      border-radius: 50%;
      border: 1px dashed rgba(91, 155, 213, 0.07);
      animation: spin 30s linear infinite reverse;
    }

    @keyframes spin {
      to {
        transform: rotate(360deg)
      }
    }

    .drone-emoji {
      font-size: 5rem;
      filter: drop-shadow(0 0 20px rgba(232, 201, 109, 0.3))
    }

    .orbit-tag {
      position: absolute;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 0.4rem 0.8rem;
      font-size: 0.75rem;
      font-weight: 600;
      white-space: nowrap;
    }

    .orbit-tag:nth-child(2) {
      top: 5%;
      left: 50%;
      transform: translateX(-50%);
      color: var(--gold)
    }

    .orbit-tag:nth-child(3) {
      bottom: 10%;
      left: 0;
      color: var(--sky-blue)
    }

    .orbit-tag:nth-child(4) {
      bottom: 20%;
      right: -5%;
      color: var(--horizon)
    }

    /* ── SERVICES ── */
    #services {
      background: var(--sky3)
    }

    .services-intro {
      max-width: 560px;
      margin-bottom: 3.5rem;
      margin-left: auto;
      margin-right: auto;
      text-align: center;
    }

    .services-intro p {
      color: var(--muted);
      font-size: 1.02rem
    }

    .services-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 1.5rem;
    }

    .service-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 2rem;
      transition: border-color 0.25s, transform 0.25s, box-shadow 0.25s;
      position: relative;
      overflow: hidden;
    }

    .service-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 100% 0%, var(--glow), transparent 60%);
      opacity: 0;
      transition: opacity 0.3s;
    }

    .service-card:hover {
      border-color: rgba(232, 201, 109, 0.4);
      transform: translateY(-5px);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4), 0 0 30px rgba(232, 201, 109, 0.06);
    }

    .service-card:hover::before {
      opacity: 1
    }

    .service-icon {
      width: 52px;
      height: 52px;
      background: linear-gradient(135deg, rgba(232, 201, 109, 0.15), rgba(255, 126, 69, 0.1));
      border: 1px solid rgba(232, 201, 109, 0.2);
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
      margin: 0 auto 1.2rem;
    }

    .service-card h3 {
      font-size: 1.05rem;
      font-weight: 600;
      margin-bottom: 0.6rem;
      text-align: left;
    }

    .service-card p {
      font-size: 0.88rem;
      color: var(--muted);
      line-height: 1.6;
      text-align: justify;
    }

    /* ── REELS ── */
    #reels {
      background: var(--sky2)
    }

    .reels-header {
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      margin-bottom: 2.5rem;
      gap: 1rem;
    }

    .reels-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1.2rem;
    }

    .reel-card {
      position: relative;
      border-radius: 14px;
      overflow: hidden;
      background: var(--card);
      border: 1px solid var(--border);
      aspect-ratio: 9/16;
    }

    .reel-card iframe {
      width: 100%;
      height: 100%;
      border: none;
    }

    @media (hover: hover) {
      .reel-card iframe {
        pointer-events: none;
      }

      .reel-card:hover iframe {
        pointer-events: all;
      }
    }

    .reel-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(180deg, transparent 30%, rgba(10, 14, 26, 0.85) 100%);
      pointer-events: none;
      transition: opacity 0.3s;
    }

    .reel-card:hover .reel-overlay {
      opacity: 0.2
    }

    .reel-label {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      padding: 1rem;
      font-size: 0.8rem;
      color: var(--text);
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 0.4rem;
    }

    .reel-label::before {
      content: '▶';
      width: 22px;
      height: 22px;
      background: rgba(232, 201, 109, 0.15);
      border: 1px solid rgba(232, 201, 109, 0.3);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.55rem;
      flex-shrink: 0;
    }

    .reels-cta {
      display: flex;
      justify-content: center;
      gap: 1rem;
      margin-top: 2.5rem;
      flex-wrap: wrap;
    }

    .btn-fb {
      padding: 0.8rem 1.8rem;
      background: linear-gradient(135deg, #1877f2, #0c5dc7);
      color: #fff;
      font-weight: 600;
      font-size: 0.88rem;
      border-radius: 50px;
      text-decoration: none;
      transition: transform 0.2s, box-shadow 0.2s;
      box-shadow: 0 4px 20px rgba(24, 119, 242, 0.3);
    }

    .btn-fb:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 28px rgba(24, 119, 242, 0.4)
    }

    .btn-yt {
      padding: 0.8rem 1.8rem;
      background: linear-gradient(135deg, #ff0000, #cc0000);
      color: #fff;
      font-weight: 600;
      font-size: 0.88rem;
      border-radius: 50px;
      text-decoration: none;
      transition: transform 0.2s, box-shadow 0.2s;
      box-shadow: 0 4px 20px rgba(255, 0, 0, 0.25);
    }

    .btn-yt:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 28px rgba(255, 0, 0, 0.35)
    }

    /* ── SOCIAL ── */
    #social {
      background: var(--sky3)
    }

    .social-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
      margin-top: 2.5rem;
      max-width: 700px;
      margin-left: auto;
      margin-right: auto;
    }

    .social-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 2rem 1.8rem;
      text-decoration: none;
      color: var(--text);
      transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .social-card:hover {
      transform: translateY(-5px)
    }

    .social-card.fb:hover {
      border-color: rgba(24, 119, 242, 0.5);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4), 0 0 30px rgba(24, 119, 242, 0.1);
    }

    .social-card.yt:hover {
      border-color: rgba(255, 0, 0, 0.4);
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.4), 0 0 30px rgba(255, 0, 0, 0.08);
    }

    .s-icon {
      width: 52px;
      height: 52px;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.4rem;
    }

    .fb .s-icon {
      background: linear-gradient(135deg, rgba(24, 119, 242, 0.2), rgba(24, 119, 242, 0.08));
      border: 1px solid rgba(24, 119, 242, 0.2)
    }

    .yt .s-icon {
      background: linear-gradient(135deg, rgba(255, 0, 0, 0.18), rgba(255, 0, 0, 0.06));
      border: 1px solid rgba(255, 0, 0, 0.15)
    }

    .s-platform {
      font-size: 0.75rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.1em;
      margin-bottom: 0.2rem
    }

    .s-handle {
      font-size: 1rem;
      font-weight: 600
    }

    .s-desc {
      font-size: 0.85rem;
      color: var(--muted);
      line-height: 1.5
    }

    .s-arrow {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      font-size: 0.8rem;
      font-weight: 600;
      margin-top: auto;
      transition: gap 0.2s;
    }

    .fb .s-arrow {
      color: #5b9bd5
    }

    .yt .s-arrow {
      color: #ff5555
    }

    .social-card:hover .s-arrow {
      gap: 0.8rem
    }

    /* ── CONTACT ── */
    #contact {
      background: var(--sky2)
    }

    .contact-wrap {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: start;
      margin-top: 3rem;
    }

    .contact-text p {
      color: var(--muted);
      line-height: 1.8;
      margin-bottom: 2rem;
      font-size: 1.02rem
    }

    .contact-links {
      display: flex;
      flex-direction: column;
      gap: 1rem
    }

    .c-link {
      display: flex;
      align-items: center;
      gap: 1rem;
      padding: 1rem 1.2rem;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 14px;
      text-decoration: none;
      color: var(--text);
      transition: border-color 0.2s, transform 0.2s;
    }

    .c-link:hover {
      border-color: rgba(232, 201, 109, 0.35);
      transform: translateX(4px)
    }

    .c-ico {
      width: 40px;
      height: 40px;
      border-radius: 10px;
      background: linear-gradient(135deg, rgba(232, 201, 109, 0.12), rgba(255, 126, 69, 0.08));
      border: 1px solid rgba(232, 201, 109, 0.15);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      flex-shrink: 0;
    }

    .c-lbl {
      font-size: 0.75rem;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.06em;
      margin-bottom: 2px
    }

    .c-val {
      font-size: 0.9rem;
      font-weight: 500
    }

    /* Contact form */
    .contact-form {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 20px;
      padding: 2.5rem;
    }

    .form-group {
      margin-bottom: 1.4rem
    }

    .form-group label {
      display: block;
      font-size: 0.8rem;
      font-weight: 500;
      color: var(--muted);
      margin-bottom: 0.5rem;
      text-transform: uppercase;
      letter-spacing: 0.06em;
    }

    .form-group input,
    .form-group textarea {
      width: 100%;
      background: rgba(255, 255, 255, 0.04);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 0.8rem 1rem;
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-size: 0.95rem;
      transition: border-color 0.2s;
      resize: vertical;
    }

    .form-group input:focus,
    .form-group textarea:focus {
      outline: none;
      border-color: rgba(232, 201, 109, 0.5);
    }

    .form-group textarea {
      min-height: 120px
    }

    .form-row {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem
    }

    .btn-send {
      width: 100%;
      padding: 0.9rem;
      background: linear-gradient(135deg, var(--gold), var(--horizon));
      color: #0a0e1a;
      font-weight: 700;
      font-size: 0.9rem;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      letter-spacing: 0.04em;
      transition: opacity 0.2s, transform 0.2s;
      box-shadow: 0 4px 20px rgba(232, 201, 109, 0.2);
    }

    .btn-send:hover {
      opacity: 0.88;
      transform: translateY(-1px)
    }

    /* ── FOOTER ── */
    footer {
      background: rgba(10, 14, 26, 0.98);
      border-top: 1px solid var(--border);
      padding: 3rem 1.5rem;
      text-align: center;
    }

    .footer-logo {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 2.5rem;
      letter-spacing: 0.08em;
      color: var(--gold);
      margin-bottom: 1rem;
    }

    .footer-links {
      display: flex;
      justify-content: center;
      gap: 2rem;
      flex-wrap: wrap;
      list-style: none;
      margin-bottom: 2rem;
    }

    .footer-links a {
      color: var(--muted);
      font-size: 0.85rem;
      text-decoration: none;
      transition: color 0.2s;
    }

    .footer-links a:hover {
      color: var(--gold)
    }

    .footer-copy {
      color: var(--muted);
      font-size: 0.8rem
    }

    .footer-copy span {
      color: var(--horizon)
    }

    /* ── REVEAL ANIMATION ── */
    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.7s ease, transform 0.7s ease
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0)
    }

    /* ── RESPONSIVE ── */
    @media(max-width:900px) {

      .about-grid,
      .contact-wrap {
        grid-template-columns: 1fr;
        gap: 2.5rem
      }

      .drone-visual {
        display: none
      }

      .altitude-badge,
      .coords-badge {
        display: none
      }

      .reels-grid {
        grid-template-columns: repeat(2, 1fr)
      }
    }

    @media(max-width:680px) {
      #nav {
        padding: 1rem 1.2rem
      }

      .nav-links,
      #nav>.btn-hire {
        display: none
      }

      .hamburger {
        display: flex
      }

      .hero {
        padding: 5rem 1.2rem 3rem
      }

      .hero h1 {
        font-size: clamp(3rem, 18vw, 5.5rem)
      }

      section {
        padding: 4rem 1.2rem
      }

      .stats-row {
        grid-template-columns: repeat(3, 1fr)
      }

      .services-grid {
        grid-template-columns: 1fr 1fr
      }

      .reels-grid {
        grid-template-columns: 1fr 1fr
      }

      .form-row {
        grid-template-columns: 1fr
      }

      .contact-form {
        padding: 1.8rem
      }
    }

    @media(max-width:440px) {
      .stats-row {
        grid-template-columns: repeat(3, 1fr);
        gap: 0.6rem;
      }

      .stat-box {
        padding: 1rem 0.5rem;
      }

      .stat-num {
        font-size: 1.8rem;
      }

      .stat-lbl {
        font-size: 0.7rem;
      }

      .services-grid {
        grid-template-columns: 1fr
      }

      .reels-grid {
        grid-template-columns: 1fr 1fr
      }

      .social-grid {
        grid-template-columns: 1fr
      }
    }
  </style>
</head>

<body>

  <!-- STARS -->
  <div class="stars" id="stars"></div>

  <!-- NAV -->
  <nav id="nav">
    <a href="#" class="nav-logo">
      <div class="drone-icon">🚁</div>
      Arafat Sajid
    </a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#reels">Reels</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <a href="#contact" class="btn-hire">Hire Me</a>
    <button class="hamburger" id="ham" aria-label="Menu">
      <span></span><span></span><span></span>
    </button>
  </nav>

  <!-- DRAWER -->
  <div class="overlay" id="overlay"></div>
  <nav class="drawer" id="drawer">
    <a href="#about" onclick="closeDrawer()">About</a>
    <a href="#services" onclick="closeDrawer()">Services</a>
    <a href="#reels" onclick="closeDrawer()">Reels</a>
    <a href="#contact" onclick="closeDrawer()">Contact</a>
    <a href="#contact" class="btn-hire" onclick="closeDrawer()">Hire Me</a>
  </nav>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-bg"></div>
    <div class="horizon-line"></div>

    <div class="hero-eyebrow">
      <span class="dot"></span>
      Drone Videographer · Bangladesh
    </div>

    <h1>
      <span class="block">Arafat</span>
      <span class="block gold">Sajid</span>
    </h1>

    <p class="hero-sub">
      Capturing <strong>Bangladesh from above</strong> — cinematic aerial footage
      that transforms ordinary scenes into extraordinary visual stories.
    </p>

    <div class="hero-cta">
      <a href="#reels" class="btn-primary">▶ Watch My Reels</a>
      <a href="#contact" class="btn-outline">Let's Work Together</a>
    </div>

    <!-- Floating badges -->
    <div class="altitude-badge">
      <div class="val">400ft</div>
      <div class="lbl">Max Altitude</div>
    </div>
    <div class="coords-badge">
      24.7471° N, 90.4203° E<br>Mymensingh, BD
    </div>

    <div class="scroll-hint">
      <div class="scroll-arrow"></div>
      Scroll
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about">
    <div class="container">
      <div class="section-tag reveal">01 — About Me</div>
      <h2 class="section-title reveal">From the Ground Up</h2>
      <div class="about-grid">
        <div class="about-text">
          <p class="reveal">
            I'm a <strong>passionate drone videographer</strong> based in Mymensingh, Bangladesh.
            With my drone in hand, I explore landscapes, events, and stories from a perspective
            most people never see — from high above, where the world looks truly beautiful.
          </p>
          <p class="reveal">
            I capture breathtaking aerial footage that transforms ordinary scenes into extraordinary
            visual stories — covering rivers, hills, real estate, events, and everything in between.
          </p>

          <div class="skills-list reveal">
            <div class="skill-row">
              <div class="skill-top"><span>Aerial Videography</span><span>98%</span></div>
              <div class="skill-track">
                <div class="skill-fill" data-w="98"></div>
              </div>
            </div>
            <div class="skill-row">
              <div class="skill-top"><span>Drone Photography</span><span>95%</span></div>
              <div class="skill-track">
                <div class="skill-fill" data-w="95"></div>
              </div>
            </div>
            <div class="skill-row">
              <div class="skill-top"><span>Cinematic Editing</span><span>92%</span></div>
              <div class="skill-track">
                <div class="skill-fill" data-w="92"></div>
              </div>
            </div>
            <div class="skill-row">
              <div class="skill-top"><span>Color Grading</span><span>88%</span></div>
              <div class="skill-track">
                <div class="skill-fill" data-w="88"></div>
              </div>
            </div>
          </div>

          <div class="stats-row reveal">
            <div class="stat-box">
              <div class="stat-num">50+</div>
              <div class="stat-lbl">Projects</div>
            </div>
            <div class="stat-box">
              <div class="stat-num">3+</div>
              <div class="stat-lbl">Years Exp</div>
            </div>
            <div class="stat-box">
              <div class="stat-num">8K+</div>
              <div class="stat-lbl">Followers</div>
            </div>
          </div>
        </div>

        <!-- Drone Visual -->
        <div class="drone-visual reveal">
          <div class="drone-circle">
            <div class="drone-emoji">🚁</div>
            <div class="orbit-tag">📍 Mymensingh</div>
            <div class="orbit-tag">🎬 4K Footage</div>
            <div class="orbit-tag">🎨 Color Graded</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- SERVICES -->
  <section id="services">
    <div class="container">
      <div class="section-tag reveal">02 — What I Do</div>
      <h2 class="section-title reveal">My Services</h2>
      <div class="services-intro reveal">
        <p>From weddings to real estate, I provide top-quality drone footage for every occasion — capturing Bangladesh
          from breathtaking new angles.</p>
      </div>

      <div class="services-grid">
        <div class="service-card reveal">
          <div class="service-icon">🏔️</div>
          <h3>Landscape & Nature</h3>
          <p>Explore Bangladesh's natural beauty through cinematic aerial shots of rivers, hills, haors, and landscapes.
          </p>
        </div>
        <div class="service-card reveal">
          <div class="service-icon">🏠</div>
          <h3>Real Estate</h3>
          <p>Stunning aerial property tours that help buyers visualize space, surroundings, and scale from above.</p>
        </div>
        <div class="service-card reveal">
          <div class="service-icon">💒</div>
          <h3>Events & Weddings</h3>
          <p>Cinematic coverage of your most memorable moments captured from perspectives impossible on the ground.</p>
        </div>
        <div class="service-card reveal">
          <div class="service-icon">📱</div>
          <h3>Social Media Reels</h3>
          <p>YouTube, Facebook, and social media reels with cinematic drone shots and expert color grading.</p>
        </div>
        <div class="service-card reveal">
          <div class="service-icon">🎨</div>
          <h3>Color Grading</h3>
          <p>Professional color correction and cinematic grading that gives your footage a polished, premium look.</p>
        </div>
        <div class="service-card reveal">
          <div class="service-icon">🗺️</div>
          <h3>Aerial Mapping</h3>
          <p>Bird's-eye coverage of sites, construction progress, and large-scale areas across Bangladesh.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- REELS -->
  <section id="reels">
    <div class="container">
      <div class="reels-header">
        <div class="section-tag reveal">03 — My Work</div>
        <h2 class="section-title reveal">Featured Reels</h2>
        <a href="https://www.facebook.com/aarafatsajid/reels" target="_blank" rel="noopener" class="btn-fb reveal">View All Reels →</a>
      </div>

      <div class="reels-grid">
        <div class="reel-card reveal">
          <iframe
            src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Freel%2F2347054125790823&show_text=false&appId"
            scrolling="no" allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
          <div class="reel-overlay"></div>
          <div class="reel-label">Aerial Reel #1</div>
        </div>
        <div class="reel-card reveal">
          <iframe
            src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Freel%2F1247380327165187&show_text=false&appId"
            scrolling="no" allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
          <div class="reel-overlay"></div>
          <div class="reel-label">Aerial Reel #2</div>
        </div>
        <div class="reel-card reveal">
          <iframe
            src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Freel%2F933135516263620&show_text=false&appId"
            scrolling="no" allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
          <div class="reel-overlay"></div>
          <div class="reel-label">Aerial Reel #3</div>
        </div>
        <div class="reel-card reveal">
          <iframe
            src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Freel%2F2703923793306875&show_text=false&appId"
            scrolling="no" allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
          <div class="reel-overlay"></div>
          <div class="reel-label">Aerial Reel #4</div>
        </div>
        <div class="reel-card reveal">
          <iframe
            src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Freel%2F1270675658336632&show_text=false&appId"
            scrolling="no" allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
          <div class="reel-overlay"></div>
          <div class="reel-label">Aerial Reel #5</div>
        </div>
        <div class="reel-card reveal">
          <iframe
            src="https://www.facebook.com/plugins/video.php?href=https%3A%2F%2Fwww.facebook.com%2Freel%2F1188587659705470&show_text=false&appId"
            scrolling="no" allowfullscreen
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
          <div class="reel-overlay"></div>
          <div class="reel-label">Aerial Reel #6</div>
        </div>
      </div>

      <div class="reels-cta">
        <a href="https://www.facebook.com/aarafatsajid" target="_blank" rel="noopener" class="btn-fb">📘 Facebook
          Page</a>
        <a href="https://www.youtube.com/@arafatssajid" target="_blank" rel="noopener" class="btn-yt">▶ YouTube
          Channel</a>
      </div>
    </div>
  </section>

  <!-- SOCIAL -->
  <section id="social">
    <div class="container">
      <div class="section-tag reveal">04 — Find Me</div>
      <h2 class="section-title reveal">Follow My Journey</h2>
      <div class="social-grid">
        <a href="https://www.youtube.com/@arafatssajid" target="_blank" rel="noopener" class="social-card yt reveal">
          <div class="s-icon">▶️</div>
          <div>
            <div class="s-platform">YouTube</div>
            <div class="s-handle">@arafatssajid</div>
          </div>
          <div class="s-desc">Watch full-length drone videos, cinematic edits, and aerial explorations of Bangladesh.
          </div>
          <div class="s-arrow">Watch now →</div>
        </a>
        <a href="https://www.facebook.com/aarafatsajid" target="_blank" rel="noopener" class="social-card fb reveal">
          <div class="s-icon">📘</div>
          <div>
            <div class="s-platform">Facebook</div>
            <div class="s-handle">aarafatsajid</div>
          </div>
          <div class="s-desc">Short reels, behind-the-scenes moments, and updates from my latest aerial shoots.</div>
          <div class="s-arrow">Follow now →</div>
        </a>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="container">
      <div class="section-tag reveal">05 — Get In Touch</div>
      <h2 class="section-title reveal">Let's Shoot Together</h2>

      <div class="contact-wrap">
        <div class="contact-text">
          <p class="reveal">Have a project in mind? Want to capture your event from the sky? I'd love to hear from you.
            Reach out and let's create something amazing.</p>
          <div class="contact-links">
            <a href="https://www.facebook.com/aarafatsajid" target="_blank" class="c-link reveal">
              <div class="c-ico">📘</div>
              <div>
                <div class="c-lbl">Facebook</div>
                <div class="c-val">facebook.com/aarafatsajid</div>
              </div>
            </a>
            <a href="https://www.youtube.com/@arafatssajid" target="_blank" class="c-link reveal">
              <div class="c-ico">▶️</div>
              <div>
                <div class="c-lbl">YouTube</div>
                <div class="c-val">youtube.com/@arafatssajid</div>
              </div>
            </a>
            <div class="c-link reveal" style="cursor:default">
              <div class="c-ico">📍</div>
              <div>
                <div class="c-lbl">Location</div>
                <div class="c-val">Bhugli, Mymensingh, Bangladesh</div>
              </div>
            </div>
          </div>
        </div>

        <div class="contact-form reveal">
          <div class="form-row">
            <div class="form-group">
              <label>Your Name</label>
              <input type="text" placeholder="John Doe">
            </div>
            <div class="form-group">
              <label>Email</label>
              <input type="email" placeholder="you@email.com">
            </div>
          </div>
          <div class="form-group">
            <label>Subject</label>
            <input type="text" placeholder="Wedding Shoot / Real Estate...">
          </div>
          <div class="form-group">
            <label>Message</label>
            <textarea placeholder="Tell me about your project..."></textarea>
          </div>
          <button class="btn-send">🚁 Send Message</button>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">Arafat Sajid</div>
    <ul class="footer-links">
      <li><a href="#about">About</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#reels">Reels</a></li>
      <li><a href="#social">Social</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <p class="footer-copy">
      © 2025 Arafat Sajid — All Rights Reserved<br>
      <span>Bhugli, Astadhar Bazar, Mymensingh, Bangladesh</span>
    </p>
  </footer>

  <script>
    // ── STARS ──
    (function () {
      const c = document.getElementById('stars');
      for (let i = 0; i < 120; i++) {
        const s = document.createElement('span');
        const size = Math.random() * 2 + 0.5;
        s.style.cssText = `
      width:${size}px;height:${size}px;
      top:${Math.random() * 100}%;left:${Math.random() * 100}%;
      --d:${3 + Math.random() * 5}s;
      --delay:-${Math.random() * 8}s;
      --op:${0.3 + Math.random() * 0.6};
    `;
        c.appendChild(s);
      }
    })();

    // ── NAV ──
    const nav = document.getElementById('nav');
    window.addEventListener('scroll', () => {
      nav.classList.toggle('scrolled', window.scrollY > 60);
    });

    // ── HAMBURGER ──
    const ham = document.getElementById('ham');
    const drawer = document.getElementById('drawer');
    const overlay = document.getElementById('overlay');
    ham.addEventListener('click', () => {
      ham.classList.toggle('open');
      drawer.classList.toggle('open');
      overlay.classList.toggle('show');
      document.body.style.overflow = drawer.classList.contains('open') ? 'hidden' : '';
    });
    overlay.addEventListener('click', closeDrawer);
    function closeDrawer() {
      ham.classList.remove('open');
      drawer.classList.remove('open');
      overlay.classList.remove('show');
      document.body.style.overflow = '';
    }

    // ── REVEAL ──
    const reveals = document.querySelectorAll('.reveal');
    const io = new IntersectionObserver(entries => {
      entries.forEach((e, i) => {
        if (e.isIntersecting) {
          // Stagger children in same parent
          const siblings = [...e.target.parentNode.querySelectorAll('.reveal:not(.visible)')];
          const idx = siblings.indexOf(e.target);
          setTimeout(() => {
            e.target.classList.add('visible');
            // Trigger skill bars
            const fills = e.target.querySelectorAll('.skill-fill');
            fills.forEach(f => f.style.width = f.dataset.w + '%');
          }, idx * 80);
          io.unobserve(e.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(r => io.observe(r));

    // ── SKILL BARS on parent reveal ──
    // Also trigger when about section itself visible
    const skillFills = document.querySelectorAll('.skill-fill');
    const skillObs = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.style.width = e.target.dataset.w + '%';
          skillObs.unobserve(e.target);
        }
      });
    }, { threshold: 0.3 });
    skillFills.forEach(f => skillObs.observe(f));

    // ── FORM SUBMIT ──
    document.querySelector('.btn-send').addEventListener('click', function () {
      const inputs = document.querySelectorAll('.contact-form input, .contact-form textarea');
      let ok = true;
      inputs.forEach(i => { if (!i.value.trim()) ok = false });
      if (!ok) { this.textContent = '⚠️ Fill in all fields'; setTimeout(() => this.textContent = '🚁 Send Message', 2000); return; }
      this.textContent = '✅ Message Sent!';
      inputs.forEach(i => i.value = '');
      setTimeout(() => this.textContent = '🚁 Send Message', 3000);
    });
  </script>
</body>

</html>
