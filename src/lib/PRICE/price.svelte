<script>
  const plans = [
    {
      type: "Hourly",
      price: "900Kč",
      period: "Hour",
      features: [
        "Immediate Flexibility and Agility",
        "Cost-Effectiveness (You only pay for what you use)",
        "Specialised Expertise on Demand",
        "Fast Delivery and Focus on Objectives",
        "External Vision and New Perspectives"
      ],
      color: "#931449" // color del fondo
    },
    {
      type: "Monthly",
      price: "80.000Kč",
      period: "Month",
      features: [
        "Commitment to Long-Term Vision",
        "Availability and Priority Dedication",
        "Responsibility and Ownership of the Code",
        "Team Loyalty and Stability",
        "Guaranteed Post-Launch Support",
        "Investment in Long-Term Product Development",
        "Availability for Non-Code Tasks",
        "Investment in Growth Potential"
      ],
      color: "#ffffff",
      textColor: "#1A202C",
      border: true
    }
  ];
</script>

<section class="pricing-section">
  <div class="container">
    <div class="heading">
      <p class="subtitle">— Pricing Table</p>
      <h2 class="title">My <span class="highlight">Pricing Model</span></h2>
    </div>

    <div class="cards">
      <!-- Custom Plan Card -->
      <div class="card custom-plan card-1">
        <h3>Hey! Need a Custom Plans?</h3>
        <p>
          Contact me to design a Custom Plan that perfectly fits your technical requirements, team size, and budget. Let's discuss your vision!
        </p>
      </div>

      {#each plans as plan, index}
        <div class="card plan-card card-{index + 2}" style="background-color: {plan.color}; color: {plan.textColor || '#fff'}; border: {plan.border ? '1px solid #E2E8F0' : 'none'}">
          <div class="plan-header">
            <span class="plan-type">{plan.type}</span>
          </div>
          <div class="plan-price">
            <span class="price">{plan.price}</span>
            <span class="period"> / {plan.period}</span>
          </div>
          <ul class="features">
            {#each plan.features as feature}
              <li>✔ {feature}</li>
            {/each}
          </ul>
        </div>
      {/each}
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

  .pricing-section {
    font-family: 'Space Grotesk', sans-serif;
    padding: 4rem 2rem;
    background: #ffffff;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
  }

  .heading .subtitle {
    color: var(--accent-red);
    font-weight: 500;
    text-transform: uppercase;
    margin-bottom: 0.5rem;
  }

  .heading .title {
    font-size: 2.5rem;
    font-weight: 700;
  }

  .highlight {
    color: var(--accent-red);
  }

  .cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    margin-top: 2rem;
    align-items: end;
  }

  .card {
    padding: 2rem;
    border-radius: 16px;
    box-shadow: 0 10px 25px rgba(77, 76, 76, 0.3);
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .card:hover {
    transform: translateY(-5px);
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.4);
  }

  /* Alturas escalonadas */
  .card-1 {
    min-height: 310px;
    margin-top: 60px;
  }

  .card-2 {
    min-height: 400px;
    margin-top: 30px;
  }

  .card-3 {
    min-height: 510px;
    margin-top: -90px;
  }

  .custom-plan {
    background: #ffffff;
    color: #1A202C;
    text-align: left;
  }

  .custom-plan h3 {
    font-weight: 800;
    margin-bottom: 0.5rem;
    font-size: 1.3rem;
  }

  .custom-plan p {
    font-size: 1rem;
    color: #4A5568;
    line-height: 1.6;
  }

  .btn {
    background-color: var(--accent-red);
    border: none;
    padding: 0.8rem 1.5rem;
    border-radius: 50px;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
    color: var(--white);
    font-family: 'Space Grotesk', sans-serif;
    margin-top: auto;
  }

  .btn:hover {
    background-color: var(--color1);
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(147, 20, 73, 0.3);
  }

  .plan-card .plan-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .plan-card .plan-type {
    font-weight: 600;
    font-size: 1rem;
  }

  .plan-card .plan-price {
    font-size: 2rem;
    font-weight: 700;
    margin: 1rem 0;
  }

  .plan-card .period {
    font-size: 1rem;
    font-weight: 400;
  }

  .plan-card .features {
    list-style: none;
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .plan-card .features li {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.95rem;
  }

  /* TABLETS */
  @media (max-width: 1024px) and (min-width: 769px) {
    .cards {
      grid-template-columns: repeat(3, 1fr);
      gap: 1.5rem;
    }

    .card-1 {
      min-height: 300px;
      margin-top: 50px;
    }

    .card-2 {
      min-height: 350px;
      margin-top: 25px;
    }

    .card-3 {
      min-height: 400px;
      margin-top: 0;
    }
  }

  /* MÓVILES Y TABLETS PEQUEÑAS */
  @media (max-width: 768px) {
    .cards {
      grid-template-columns: 1fr;
      gap: 2rem;
      align-items: stretch;
    }

    /* En móvil, eliminamos el efecto escalonado y margins */
    .card-1,
    .card-2,
    .card-3 {
      min-height: auto;
      margin-top: 0;
    }

    .heading .title {
      font-size: 2rem;
    }

    .custom-plan h3 {
      font-size: 1.2rem;
    }
  }

  @media (max-width: 480px) {
    .pricing-section {
      padding: 3rem 1rem;
    }

    .heading .title {
      font-size: 1.8rem;
    }

    .card {
      padding: 1.5rem;
    }

    .custom-plan h3 {
      font-size: 1.1rem;
    }

    .custom-plan p {
      font-size: 0.95rem;
    }

    .plan-card .plan-price {
      font-size: 1.8rem;
    }
  }
</style>