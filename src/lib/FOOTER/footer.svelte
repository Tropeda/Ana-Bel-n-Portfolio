<script>
  const year = new Date().getFullYear();

  const socialLinks = [
    {
      icon: "/in.png",
      name: "LinkedIn",
      url: "https://www.linkedin.com/in/ana-belen-r-7b650710b/"
    },
    {
      icon: "/email.png",
      name: "Gmail",
      url: "mailto:anabelenr84@gmail.com"
    }
  ];

  const navigation = ["Home", "Services", "About", "Projects", "Quote", "Questions", "Contact"];
</script>

<footer class="footer">
  <div class="footer-content">
    <!-- Columna 1 -->
    <div class="footer-section brand">
      <div class="logo">
        <div class="logo-circle">
          <img src="/logo.png" alt="Logo Ana Belén" class="logo-img" />
        </div>
        <h3>Ana Belén Rodríguez Rodríguez</h3>
      </div>

      <div class="socials">
        {#each socialLinks as link}
          <a href={link.url} title={link.name} target="_blank" rel="noopener noreferrer">
            {#if link.icon.endsWith(".png") || link.icon.endsWith(".jpg") || link.icon.endsWith(".svg")}
              <img src={link.icon} alt={link.name} class="social-img" />
            {:else}
              <span class="social-emoji">{link.icon}</span>
            {/if}
          </a>
        {/each}
      </div>
    </div>

    <!-- Columna 3 -->
    <div class="footer-section">
      <h4>Contact</h4>
      <ul>
        <li>+420 608 188 684</li>
        <li>anabelenr84@gmail.com</li>
      </ul>
    </div>

  </div>

  <div class="footer-bottom">
    <p>Copyright © {year} <span class="brand-name">Ana</span>. All Rights Reserved.</p>
  </div>
</footer>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700;900&display=swap');

  :root {
    --color1: #060408;
    --color2: #312935;
    --color3: #696377;
    --color4: #a7a4b6;
    --color5: #ead9e7;
    --accent-red: rgb(147, 20, 73);
    --white: #ffffff;
  }

  .footer {
    background: var(--color1);
    color: var(--white);
    font-family: 'Lato', sans-serif;
    padding: 4rem 5% 2rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }

  .footer-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 2rem 3rem;
    margin-bottom: 2rem;
  }

  .footer-section h4 {
    color: var(--accent-red);
    font-weight: 900;
    margin-bottom: 1rem;
    font-size: 1.2rem;
    margin-left: 25rem;
  }

  .footer-section ul {
    list-style: none;
    padding: 0;
    margin: 0;
    margin-left: 25rem;
  }

  .footer-section ul li {
    margin-bottom: 0.6rem;
    color: var(--white);
    font-size: 0.95rem;
  }

  /* BRAND */
  .brand .logo {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    margin-bottom: 1rem;
  }

  .logo-circle {
    width: 60px;
    height: 60px;
    background: var(--white);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 15px rgba(255, 255, 255, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .logo-circle:hover {
    transform: scale(1.05);
    box-shadow: 0 6px 20px rgba(255, 255, 255, 0.2);
  }

  .logo-img {
    width: 75px;
    height: 38px;
    object-fit: contain;
  }

  .brand h3 {
    font-size: 1.4rem;
    font-weight: 700;
  }

  /* SOCIALS */
  .socials a {
    background: var(--white);
    color: white;
    font-size: 1.1rem;
    border-radius: 50%;
    padding: 0.6rem;
    margin-right: 0.5rem;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.3s, background 0.3s;
    width: 36px;
    height: 36px;
  }

  .socials a:hover {
    transform: translateY(-3px);
    background: var(--color3);
  }

  .socials .social-img {
    width: 24px;
    height: 24px;
    object-fit: contain;
  }

  .socials .social-emoji {
    font-size: 1.2rem;
  }


  /* FOOTER BOTTOM */
  .footer-bottom {
    border-top: 1px solid rgba(255, 255, 255, 0.2);
    padding-top: 1.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    text-align: center;
    color: var(--color4);
    font-size: 0.9rem;
    margin-left: 32rem;
  }

  .footer-bottom .brand-name {
    color: var(--accent-red);
    font-weight: 600;
  }

  @media (min-width: 768px) {
    .footer-bottom {
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      text-align: left;
    }
  }
</style>
