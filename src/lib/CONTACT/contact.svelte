<script>
  const phone = "+420 608 188 684";
  const email = "anabelenr84@gmail.com";
  const linkedin = "https://www.linkedin.com/in/ana-belen-r-7b650710b/";
  const address = "Hlavní město, Praha";
</script>

<section id="contact">
  <div class="contact-container">
    <!-- Fondo con efecto -->
    <div class="background-image"></div>
    <div class="background-overlay"></div>

    <!-- Card de contacto -->
    <div class="contact-card">
      <p class="subtitle">— Contact Me</p>
      <h2 class="title">
        Let's <span class="highlight">Connect & Collaborate</span>
      </h2>
      <p class="description">
        Turn your vision into reality. Write to me and let's collaborate.
      </p>

      <div class="contact-list">
        <a href={`tel:${phone}`} class="contact-item">
          <span class="icon"><img src="phone.png" alt="phone icon"></span>
          <span>{phone}</span>
        </a>

        <a href={`mailto:${email}`} class="contact-item">
          <span class="icon"><img src="email.png" alt="email icon"></span>
          <span>{email}</span>
        </a>

        <a href={linkedin} target="_blank" rel="noopener noreferrer" class="contact-item">
          <span class="icon"><img src="in.png" alt="LinkedIn icon"></span>
          <span>LinkedIn</span>
        </a>

        <div class="contact-item">
          <span class="icon"><img src="mapa.png" alt="map icon"></span>
          <span>{address}</span>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
  :root {
    --color1: #060408;
    --color2: #312935;
    --color3: #696377;
    --color4: #a7a4b6;
    --color5: #ead9e7;
    --accent-red: #931449;
    --white: #ffffff;
  }

  .contact-container {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Lato', sans-serif;
    overflow: hidden;
  }

  .background-image {
    background: url(contact.png);
    position: absolute;
    inset: 0;
    filter: brightness(0.6) blur(3px);
    transform: scale(1.1);
    z-index: 0;
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
  }

  .contact-card {
    position: relative;
    z-index: 1;
    max-width: 420px;
    width: 100%;
    text-align: left;
    padding: 2.5rem;
    background: rgba(147, 20, 73, 0.9);
    border-radius: 20px;
    backdrop-filter: blur(8px);
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
    animation: fadeInUp 0.8s ease-out;
  }

  .subtitle {
    color: white;
    font-weight: 700;
    font-size: large;
  }

  .title {
    font-size: 2rem;
    font-weight: 700;
    margin: 0.5rem 0 1.5rem;
    line-height: 1.3;
  }

  .highlight {
    color: var(--white);
  }

  .description {
    font-size: 1.05rem;
    color: #e0e0e0;
  }

  .contact-list {
    margin-top: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }

  .contact-item {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    background: var(--color2);
    padding: 0.9rem 1.2rem;
    border-radius: 12px;
    text-decoration: none;
    color: white;
    transition: transform 0.2s, background 0.3s;
  }

  .contact-item:hover {
    background: var(--color3);
    transform: translateY(-3px);
  }

  .icon {
    background: white;
    color: var(--accent-red);
    padding: 0.2rem;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 32px;
    height: 32px;
  }

  .icon img {
    width: 25px;
    height: 25px;
    object-fit: contain;
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(30px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
</style>
