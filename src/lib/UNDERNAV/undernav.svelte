<script>
  const items = ["Web Design", "Developer"];
</script>

<div class="marquee">
  <div class="track">
    {#each Array(10).fill(items).flat() as item, i}
      <span class="text">{item}</span>
      <span class="separator">✦</span>
    {/each}
  </div>
</div>

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
  
  :global(body) {
    overflow-x: hidden;
    margin: 0;
  }

  :global(html) {
    overflow-x: hidden;
  }

  .marquee {
    overflow: hidden;
    background-color: var(--accent-red); 
    width: 100%;
    padding: 1rem 0;
    white-space: nowrap;
    position: relative;
  }

  .track {
    display: flex;
    gap: 1rem;
    animation: scroll 20s linear infinite;
    will-change: transform;
  }

  .text {
    color: white;
    font-size: 1.2rem;
    font-weight: 500;
    font-family: 'Lato', sans-serif;
  }

  .separator {
    color: #111;
  }

  @keyframes scroll {
    from {
      transform: translateX(0);
    }
    to {
      transform: translateX(-50%);
    }
  }
</style>