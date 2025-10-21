<script>
  // Variable para controlar si el menú está abierto o cerrado
  let menuOpen = false;
  let showScrollTop = false;

  // Función para alternar el estado del menú
  function toggleMenu() {
    menuOpen = !menuOpen;
  }

  // Función para mostrar/ocultar el botón de scroll to top
  function handleScroll() {
    showScrollTop = window.scrollY > 300;
  }

  // Función para ir hacia arriba
  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  // Agregar listener de scroll cuando el componente se monta
  if (typeof window !== 'undefined') {
    window.addEventListener('scroll', handleScroll);
  }

  // Función para scroll suave
  /**
   * @param {(MouseEvent & { currentTarget: EventTarget & HTMLAnchorElement; }) | (MouseEvent & { currentTarget: EventTarget & HTMLButtonElement; })} event
   * @param {string} sectionId
   */
  function scrollToSection(event, sectionId) {
    event.preventDefault(); // Evita el salto brusco
    const section = document.querySelector(sectionId);
    if (section) {
      section.scrollIntoView({ behavior: "smooth", block: "start" });
    }
    menuOpen = false; // Cierra el menú en móvil tras hacer clic
  }
</script>

<nav class="navbar">
  <div class="logo">
    <img src="logo.png" alt="Logo" class="logo-image" />
  </div>

  <button class="hamburger-menu" on:click={toggleMenu}>☰</button>

  <div class="menu-container" class:open={menuOpen}>
    <ul class="nav-links">
      <li><a href="#services" on:click={(e) => scrollToSection(e, '#services')}>Services</a></li>
      <li><a href="#about" on:click={(e) => scrollToSection(e, '#about')}>About</a></li>
      <li><a href="#projects" on:click={(e) => scrollToSection(e, '#projects')}>Projects</a></li>
    <li><a href="#projects" on:click={(e) => scrollToSection(e, '#questions')}>Questions</a></li>
    </ul>
    <button class="contact-button" on:click={(e) => scrollToSection(e, '#contact')}>
      Contact Me
    </button>
  </div>
</nav>

<!-- Botón de Scroll to Top -->
{#if showScrollTop}
  <button class="scroll-top-btn" on:click={scrollToTop} title="Volver arriba">
    ↑
  </button>
{/if}

<style>
  @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');

  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :global(html) {
    scroll-behavior: smooth; /* Por si acaso, activa scroll suave global */
  }

  :root {
    --color1: #060408;
    --color2: #312935;
    --color3: #696377;
    --color4: #a7a4b6;
    --color5: #ead9e7;
    --accent-red: rgb(147, 20, 73);
  }

  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 3rem;
    background-color: var(--accent-red);
    font-family: 'Lato', sans-serif;
    width: 100vw;
    margin: 0;
    box-sizing: border-box;
    position: relative;
    left: 50%;
    right: 50%;
    margin-left: -50vw;
    margin-right: -50vw;
    z-index: 100;
  }

  .logo-image {
    height: 45px;
  }

  .menu-container {
    display: flex;
    align-items: center;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
  }

  .nav-links a {
    text-decoration: none;
    color: var(--color5);
    font-size: 1rem;
    font-weight: 600;
    position: relative;
    transition: color 0.3s ease;
    cursor: pointer;
  }

  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 0;
    height: 2px;
    background-color: var(--color1);
    transition: width 0.3s ease;
  }

  .nav-links a:hover {
    color: var(--color1);
  }

  .nav-links a:hover::after {
    width: 100%;
  }

  .contact-button {
    background-color: var(--color5);
    color: var(--accent-red);
    border: none;
    padding: 0.8rem 1.8rem;
    border-radius: 9999px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    margin-left: 2rem;
  }

  .contact-button:hover {
    background-color: var(--color1);
    color: var(--color5);
  }

  .scroll-top-btn {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    width: 50px;
    height: 50px;
    background-color: var(--accent-red);
    color: var(--color5);
    border: none;
    border-radius: 50%;
    font-size: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    transition: all 0.3s ease;
    z-index: 999;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .scroll-top-btn:hover {
    background-color: var(--color1);
    transform: translateY(-3px);
    box-shadow: 0 6px 16px rgba(0, 0, 0, 0.4);
  }

  .scroll-top-btn:active {
    transform: translateY(-1px);
  }

  .hamburger-menu {
    display: none;
  }

  /* --- Responsivo (Móvil) --- */
  @media (max-width: 768px) {
    .navbar {
      padding: 1rem 1.5rem;
      flex-wrap: wrap;
    }

    .menu-container {
      display: none;
      flex-direction: column;
      align-items: center;
      width: 100%;
      padding-top: 1rem;
      background-color: var(--accent-red);
    }

    .menu-container.open {
      display: flex;
    }

    .hamburger-menu {
      display: block;
      background: none;
      border: none;
      font-size: 2rem;
      cursor: pointer;
      color: var(--color5);
      padding: 0;
      line-height: 1;
    }

    .nav-links {
      flex-direction: column;
      width: 100%;
      text-align: center;
      gap: 1rem;
      margin-bottom: 1rem;
    }

    .contact-button {
      width: 90%;
      margin-left: 0;
    }

    .scroll-top-btn {
      width: 45px;
      height: 45px;
      bottom: 1.5rem;
      right: 1.5rem;
      font-size: 1.3rem;
    }
  }
</style>