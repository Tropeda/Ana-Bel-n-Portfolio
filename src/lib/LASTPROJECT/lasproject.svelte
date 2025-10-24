<script>
  let projects = [
    {
      id: 1,
      title: 'WEBSITE FOR DEVELOPERS',
      description: 'Designed and developed a website from scratch for a startup specialized in creating websites for other companies. The result was a modern, attractive, and functional platform that reinforced the brand\'s digital presence, helped build trust, and attracted new clients. The website was built with scalability in mind, allowing the company to easily showcase their services and portfolio as they continue to grow. By combining clean design with strong functionality, the project not only met the client\'s expectations but also set a solid foundation for their digital identity.',
      tags: ['Design', 'Web Development', 'Brand Identity'],
      image: 'lasproject.png',
      reverse: false
    }
    
    
  ];
</script>

<main>
  <section id="projects"> </section>
  <section class="projects-section">
    <div class="content-wrapper"> 
      <header class="header-container">
        <div class="title-row">
          <h2 class="main-title">
            <span class="black-text">My</span> Latest Project
          </h2>
        </div>
      </header>

      <div class="cards-container">
        {#each projects as project (project.id)}
          <div class="project-card" class:reverse={project.reverse}>
            <div class="image">
              <img src={project.image} alt={project.title} />
            </div>
            <div class="info">
              <h3>{project.title}</h3>
              <p>{project.description}</p>
              <ul>
                {#each project.tags as tag}
                  <li>{tag}</li>
                {/each}
              </ul>
            </div>
          </div>
        {/each}
      </div>
    </div>

  </section>
</main>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Dancing+Script:wght@700&display=swap');
  
  :root {
    --color1: #060408;
    --color2: #312935;
    --color3: #696377;
    --color4: #a7a4b6;
    --color5: #ead9e7;
    --accent-red: #931449;
    --white: #ffffff;
  }

  .projects-section {
    background-color: var(--accent-red);
    padding: 60px 5% 2%; 
    font-family: 'Lato', sans-serif;
    position: relative;
  }

  .content-wrapper {
    max-width: 1400px;
    margin: 0 auto;
  }

  .cards-container {
    display: flex;
    flex-direction: column;
    gap: 40px;
    margin-bottom: 60px;
  }

  .project-card {
    display: flex;
    gap: 20px;
    background: #eeb7d1;
    border-radius: 12px;
    overflow: hidden;
    padding: 15px;
    color: var(--color-white);
  }

  .project-card.reverse {
    flex-direction: row-reverse;
  }

  .image {
    flex: 1;
    overflow: hidden;
    border-radius: 8px;
    min-height: 200px;
  }

  .image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
  }

  .info {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-top: -100px;
  }

  .info h3 {
    margin: 110px 0 18px 40px;
    font-size: 2rem;
    text-align: left;
    font-family: 'Lato', sans-serif;
    color: rgb(70, 70, 70);
  }

  .info p {
    padding: 8%;
    margin: -50px 0 -50px -10px;
    color: var(--color1);
    line-height: 1.6;
  }

  ul {
    padding: 25px;
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-left: 15px;
  }

  li {
    background: rgba(255,255,255,0.2);
    padding: 5px 10px;
    border-radius: 6px;
    font-size: 0.9rem;
    font-family: 'Lato', sans-serif;
  }

  .title-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 40px;
  }

  .main-title {
    color: var(--color5);
    font-size: 2.5rem;
    font-weight: 700;
  }

  .black-text {
    color: var(--color1); 
  }

  .view-all-button {
    background-color: var(--color-light-green);
    color: var(--white);
    border: none;
    padding: 10px 20px;
    border-radius: 20px;
    cursor: pointer;
    font-weight: bold;
    display: flex;
    align-items: center;
    transition: background-color 0.2s;
  }

  .view-all-button:hover {
    background-color: var(--color5);
    color: var(--color1);
  }

  .arrow-icon {
    margin-left: 8px;
    margin-top: -4.5px;
    font-size: 1.2rem;
    transition: transform 0.2s;
  }

  .view-all-button:hover .arrow-icon {
    transform: translateX(5px);
  }


  /* Monitores grandes (1920px+) */
  @media (min-width: 1920px) {
    .projects-section {
      padding: 80px 10% 20px;
    }

    .content-wrapper {
      max-width: 1800px;
    }

    .main-title {
      font-size: 3rem;
      margin-top: -30px;
    }

    .info h3 {
      font-size: 2.5rem;
      margin: 120px 0 20px 50px;
    }

    .info p {
      font-size: 1.1rem;
      line-height: 1.8;
    }

    .cards-container {
      gap: 60px;
      margin-bottom: 80px;
    }

  }

  /* Tablets horizontales (768px - 1024px) */
  @media (max-width: 1024px) and (min-width: 769px) {
    .projects-section {
      padding: 50px 4% 20px;
    }

    .main-title {
      font-size: 2.2rem;
    }

    .info h3 {
      font-size: 1.8rem;
      margin: 115px 0 15px 30px;
    }

    .info p {
      font-size: 0.80rem;
      padding: 6%;
      margin: -20px 0 -40px -10px;
    }

    ul {
      padding: 20px;
      margin-left: 10px;
      margin-top: 15px;
    }

    li {
      font-size: 0.85rem;
    }
  }

  /* Tablets verticales (600px - 768px) */
  @media (max-width: 768px) {
    .projects-section {
      padding: 40px 4% 20px;
    }

    .project-card {
      flex-direction: column;
      padding: 12px;
    }
    
    .project-card.reverse {
      flex-direction: column;
    }

    .image {
      min-height: 250px;
    }

    .info h3 {
      margin: 100px 0 10px 20px;
      font-size: 1.6rem;
    }

    .info p {
      padding: 5%;
      margin: 0.5px 0;
      font-size: 0.9rem;
      line-height: 1.5;
    }

    ul {
      padding: 15px;
      margin-left: 5px;
    }

    .main-title {
      font-size: 2rem;
    }

    .cards-container {
      gap: 30px;
      margin-bottom: 50px;
    }
    
  }

  /* Móviles (menos de 600px) */
  @media (max-width: 600px) {
    .projects-section {
      padding: 30px 3% 20px;
    }

    .title-row {
      flex-direction: column;
      align-items: flex-start;
      gap: 15px;
    }

    .main-title {
      font-size: 1.8rem;
       margin-left: 15px;
    }
    
    .view-all-button {
      padding: 8px 16px;
      font-size: 0.9rem;
    }

    .project-card {
      gap: 15px;
      padding: 10px;
    }

    .image {
      min-height: 200px;
    }

    .info h3 {
      margin: 15px 0 8px 15px;
      font-size: 1.4rem;
      margin-top: 100px;
    }

    .info p {
      padding: 4%;
      margin: 8px 0;
      font-size: 0.85rem;
      line-height: 1.4;
    }

    ul {
      padding: 10px;
      margin-left: 0;
      gap: 8px;
    }

    li {
      font-size: 0.8rem;
      padding: 4px 8px;
    }

    .cards-container {
      gap: 25px;
      margin-bottom: 40px;
    }

  }

  /* Móviles pequeños (menos de 400px) */
  @media (max-width: 400px) {
    .projects-section {
      padding: 25px 2% 20px;
    }

    .main-title {
      font-size: 1.5rem;
      margin-left: 15px;
    }

    .info h3 {
      font-size: 1.2rem;
      margin: 12px 0 6px 10px;
      margin-top: 100px;
    }

    .info p {
      font-size: 0.8rem;
      margin-top: 10px;
    }

    li {
      font-size: 0.75rem;
    }

  }
</style>