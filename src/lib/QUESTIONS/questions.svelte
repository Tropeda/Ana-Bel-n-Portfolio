<script>
  let faqs = [
    {
      question: "What industries have you worked in as a product designer?",
      answer: "I've worked across diverse industries, including technology, e-commerce, and creative digital services.",
      open: false
    },
    {
      question: "Can I download your resume/CV for information ?",
      answer: "Certainly! You can download my resume/CV directly from my website. It provides a comprehensive overview of my education, work experience, and design achievements.",
      open: false
    },
    {
      question: "Are you available for freelance design work ?",
      answer: "Yes, I am open to freelance opportunities. Feel free to contact me to discuss your project needs.",
      open: false
    },
    {
      question: "What tools do you use for your design work?",
      answer: "I mainly use Figma, Adobe XD, Illustrator, and Photoshop, combined with prototyping and collaboration tools.",
      open: false
    },
    {
      question: "How do I navigate through your portfolio projects?",
      answer: "My portfolio is structured with categories and filters, making it easy to browse projects by type or industry.",
      open: false
    }
  ];

  /**
   * @param {number} index
   */
  function toggleFAQ(index) {
    faqs = faqs.map((faq, i) => ({
      ...faq,
      open: i === index ? !faq.open : faq.open
    }));
  }
</script>
<section id="questions"> </section>
<section class="faq-section">
  <div class="container">
    <p class="subtitle">— FAQs</p>
    <h2 class="title">Questions? <span>Look here.</span></h2>

    <div class="faq-list">
      {#each faqs as faq, i}
        <!-- svelte-ignore a11y_click_events_have_key_events -->
        <!-- svelte-ignore a11y_no_static_element_interactions -->
        <div
          class="faq-item {faq.open ? 'open' : ''}"
          on:click={() => toggleFAQ(i)}
        >
          <div class="faq-question">
            <span>{faq.question}</span>
            <span class="icon">{faq.open ? "−" : "+"}</span>
          </div>
          {#if faq.open}
            <div class="faq-answer">
              <p>{faq.answer}</p>
            </div>
          {/if}
        </div>
      {/each}
    </div>
  </div>
</section>

<style>

    @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');


  :root {
        --color1: #060408;
        --color2: #312935;
        --color3: #696377;
        --color4: #a7a4b6;
        --color5: #ead9e7;
        --accent-red: rgb(147, 20, 73);
    }


  .faq-section {
    padding: 4rem 2rem;
    background:white;
    font-family: 'Lato', sans-serif;
    color: var(--white);
    text-align: center;
    color: white;
  }

  .subtitle {
    font-size: 0.9rem;
    text-transform: uppercase;
    opacity: 0.9;
    margin-bottom: 0.5rem;
    color: var(--color3);
  }

  .title {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 2rem;
    color: var(--color1);
  }

  .title span {
    color: var(--accent-red);
  }

  .faq-list {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    max-width: 800px;
    margin: 0 auto;
    text-align: left;
  }

  .faq-item {
    background: var(--accent-red);
    border-radius: 8px;
    padding: 1rem 1.5rem;
    cursor: pointer;
    transition: background 0.3s ease;
  }

  .faq-item.open {
    background: var(--color1);
    color: var(--color5);
  }

  .faq-question {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-weight: 600;
    font-size: 1.1rem;
  }

  .faq-answer {
    margin-top: 0.75rem;
    font-size: 0.95rem;
    line-height: 1.6;
  }

  .icon {
    font-size: 1.5rem;
    font-weight: bold;
  }

  @media (max-width: 600px) {
    .title {
      font-size: 2rem;
    }
  }
</style>