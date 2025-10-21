
<script>
  // Aquí defines los iconos que quieras usar
  let educationIcon = "educacion.png";   // Cambia por la ruta de tu icono
  let workIcon = "trabajo.png";             // Cambia por la ruta de tu icono

  let education = [
    {
      institution: "University of Malaga",
      degree: "",
      period: "2018 - 202"
    },
    {
      institution: "Aurora Academy",
      degree: "Bachelor in Visual Arts",
      period: "2008 - 2012"
    },
    {
      institution: "Crystalbrook",
      degree: "High School",
      period: "1996 - 2008"
    }
  ];

  let workExperience = [
    {
      company: "Insightlancer",
      position: "Senior Product Designer",
      period: "2018 - 2024"
    },
    {
      company: "Self-Employed",
      position: "Visual Artist",
      period: "2016 - 2018"
    },
    {
      company: "KG Graphics Studio",
      position: "Web Designer",
      period: "2014 - 2016"
    }
  ];
</script>

<section class="education-work-section">
  <div class="section-header">
    <span class="dash">—</span>
    <span class="subtitle">Education & Work</span>
  </div>
  
  <h2 class="section-title">
    My <span class="highlight">Education</span> & <span class="highlight">Work Experience</span>
  </h2>

  <div class="content-grid">
    <!-- Education Column -->
    <div class="column">
      <div class="column-header">
        <div class="icon-circle">
          <img src={educationIcon} alt="Education Icon" class="custom-icon"/>
        </div>
        <h3>Education</h3>
      </div>

      <div class="timeline">
        {#each education as edu}
          <div class="timeline-item">
            <div class="item-header">
              <h4 class="item-title">{edu.institution}</h4>
              <span class="item-period">{edu.period}</span>
            </div>
            <p class="item-subtitle">{edu.degree}</p>
          </div>
        {/each}
      </div>
    </div>

    <!-- Work Experience Column -->
    <div class="column">
      <div class="column-header">
        <div class="icon-circle">
          <img src={workIcon} alt="Work Icon" class="custom-icon"/>
        </div>
        <h3>Work Experience</h3>
      </div>

      <div class="timeline">
        {#each workExperience as work}
          <div class="timeline-item">
            <div class="item-header">
              <h4 class="item-title">{work.company}</h4>
              <span class="item-period">{work.period}</span>
            </div>
            <p class="item-subtitle">{work.position}</p>
          </div>
        {/each}
      </div>
    </div>
  </div>
</section>

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

  .education-work-section {
    background: white;
    padding: 1rem 2rem;
    font-family: 'Space Grotesk', sans-serif;
    margin-bottom: 40px;
  }

  .section-header {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    margin-bottom: 1rem;
  }

  .dash {
    color: #2d3748;
    font-weight: 600;
    font-size: 1.5rem;
  }

  .subtitle {
    color: #4a5568;
    font-size: 0.95rem;
    font-weight: 500;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  .section-title {
    font-size: 3rem;
    font-weight: 700;
    color: #1a202c;
    text-align: center;
    margin-bottom: 4rem;
    line-height: 1.2;
  }

  .highlight {
    color: var(--accent-red);
  }

  .content-grid {
    max-width: 1200px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(450px, 1fr));
    gap: 3rem;
  }

  .column {
    background: var(--color5);
    border-radius: 1.5rem;
    padding: 2.5rem;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  }

  .column-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 2.5rem;
  }

  .icon-circle {
    width: 60px;
    height: 60px;
    background: var(--accent-red);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    overflow: hidden;
  }

  .custom-icon {
    width: 32px;
    height: 32px;
    object-fit: contain;
  }

  .column-header h3 {
    font-size: 1.8rem;
    font-weight: 700;
    color: var(--accent-red);
    margin: 0;
  }

  .timeline {
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }

  .timeline-item {
    padding-bottom: 2rem;
    border-bottom: 2px solid #e2e8f0;
  }

  .timeline-item:last-child {
    border-bottom: none;
    padding-bottom: 0;
  }

  .item-header {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    margin-bottom: 0.5rem;
    gap: 1rem;
  }

  .item-title {
    font-size: 1.4rem;
    font-weight: 700;
    color: #1a202c;
    margin: 0;
  }

  .item-period {
    font-size: 1rem;
    font-weight: 600;
    color: #718096;
    white-space: nowrap;
  }

  .item-subtitle {
    font-size: 1.05rem;
    color: #718096;
    margin: 0;
    line-height: 1.6;
  }

  @media (max-width: 1024px) {
    .content-grid {
      grid-template-columns: 1fr;
      gap: 2rem;
    }
  }

  @media (max-width: 768px) {
    .education-work-section {
      padding: 3rem 1.5rem;
    }

    .section-title {
      font-size: 2rem;
      margin-bottom: 3rem;
    }

    .content-grid {
      grid-template-columns: 1fr;
    }

    .column {
      padding: 2rem 1.5rem;
    }

    .column-header h3 {
      font-size: 1.5rem;
    }

    .item-title {
      font-size: 1.2rem;
    }

    .item-header {
      flex-direction: column;
      gap: 0.5rem;
    }

    .item-period {
      align-self: flex-start;
    }
  }
</style>

