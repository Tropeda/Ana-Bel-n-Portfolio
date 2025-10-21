<script>
    // Función para scroll suave a secciones
    /**
   * @param {string} sectionId
   */
    function scrollToSection(sectionId) {
        const section = document.querySelector(sectionId);
        if (section) {
            section.scrollIntoView({ behavior: "smooth", block: "start" });
        }
    }

    // Funcionalidad mejorada para los botones
    function handlePortfolio() {
        scrollToSection('#projects');
    }

    function handleHireMe() {
        scrollToSection('#contact');
    }

    // Efecto parallax suave para el círculo
    let scrollY = 0;
</script>

<svelte:window bind:scrollY />

<section class="hero-section">
    <div class="content-wrapper">
        <p class="greeting">— Hello</p>
        <h1 class="title">
            I'm <span class="highlight">Ana</span>,<br>
            <span class="profession">Web developer</span>
        </h1>
        
        <div class="buttons-container">
            <button class="btn primary-btn" on:click={handlePortfolio}>
                <span>Portfolio</span>
                <span class="arrow">→</span>
            </button>
        </div>
    </div>

    <div class="image-wrapper">
        <div class="image-container">
            <img src="foto-perfil.png" alt="Ana - Web Developer" class="profile-image">
            <div class="decorative-shape"></div>
            <div class="floating-elements">
                <div class="dot dot-1"></div>
                <div class="dot dot-2"></div>
                <div class="dot dot-3"></div>
            </div>
        </div>
    </div>

    <div class="hire-me-circle-wrapper" 
         style="transform: translateY({scrollY * 0.1}px)" 
         on:click={handleHireMe}
         on:keydown={(e) => e.key === 'Enter' && handleHireMe()}
         role="button"
         tabindex="0">
        <svg viewBox="0 0 100 100" class="circular-text-svg">
            <path id="circlePath" fill="none" stroke="none" 
                  d="M 50, 50 m -35, 0 a 35,35 0 1,1 70,0 a 35,35 0 1,1 -70,0" />
            <text fill="#ead9e7" font-family="Lato, sans-serif" font-size="7" letter-spacing="0.5" font-weight="700">
                <textPath href="#circlePath" startOffset="25%">
                    HIRE ME • HIRE ME • HIRE ME •
                </textPath>
            </text>
        </svg>
        <div class="inner-circle">
           
        </div>
    </div>

    <div class="background-grid"></div>
    <div class="background-blur-1"></div>
    <div class="background-blur-2"></div>
</section>

<style>
/* Importamos la fuente Lato */
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700;900&display=swap');

/* Variables de color actualizadas */
:root {
    --color1: #060408;
    --color2: #312935;
    --color3: #696377;
    --color4: #a7a4b6;
    --color5: #ead9e7;
    --accent-red: rgb(147, 20, 73);
    --white: #ffffff;
}

.hero-section {
    position: relative;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0rem;
    align-items: center;
    min-height: 85vh;
    background: linear-gradient(135deg, var(--white) 0%, #fafafa 100%);
    color: var(--color1);
    font-family: 'Lato', sans-serif;
    padding: 5rem 8rem;
    overflow: hidden;
    z-index: 1;
}

/* Contenido principal */
.content-wrapper {
    z-index: 10;
    max-width: 600px;
    animation: fadeInUp 0.8s ease-out;
    margin-left: -70px;
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

.greeting {
    font-size: 1.2rem;
    font-weight: 400;
    color: var(--color3);
    margin-bottom: 1rem;
    text-transform: uppercase;
    letter-spacing: 2px;
    margin-left: 15rem;
}

.title {
    font-size: clamp(3rem, 5vw, 5.5rem);
    line-height: 1.1;
    font-weight: 900;
    color: var(--color1);
    margin: 0rem 0rem 1.5rem 15rem;
}

.highlight {
    color: var(--accent-red);
    position: relative;
    display: inline-block;
}

.highlight::after {
    content: '';
    position: absolute;
    bottom: 0.05em;
    left: 0;
    width: 100%;
    height: 0.1em;
    background: linear-gradient(90deg, var(--accent-red), rgba(147, 20, 73, 0.3));
    z-index: -1;
    border-radius: 3px;
    transform: scaleX(0);
    transform-origin: left;
    animation: underlineGrow 0.8s ease-out 0.5s forwards;
}

@keyframes underlineGrow {
    to {
        transform: scaleX(1);
    }
}

.profession {
    background: linear-gradient(135deg, var(--color1), var(--color2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.buttons-container {
    display: flex;
    gap: 1.5rem;
    flex-wrap: wrap;
    margin-left: 215px;
}

.btn {
    padding: 1.2rem 2.5rem;
    border: none;
    border-radius: 50px;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
    position: relative;
    overflow: hidden;
    font-family: 'Lato', sans-serif;
    margin-left: 30px;
}

.btn::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.5s;
}

.btn:hover::before {
    left: 100%;
}

.btn:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 25px rgba(0,0,0,0.15);
}

.primary-btn {
    background: linear-gradient(135deg, var(--accent-red), #b91c5c);
    color: var(--white);
    display: flex;
    align-items: center;
    gap: 0.8rem;
    box-shadow: 0 4px 15px rgba(147, 20, 73, 0.3);
}

/* Contenedor de imagen mejorado */
.image-wrapper {
    display: flex;
    /* MODIFICACIÓN 1: Cambié justify-content de center a flex-start para mover la imagen más a la izquierda */
    justify-content: center;
    /* MODIFICACIÓN 2: Cambié align-items de center a flex-start para subir la imagen */
    align-items: flex-start;
    position: relative;
    z-index: 5;
    /* MODIFICACIÓN 3: Agregué margin-left negativo para mover la imagen aún más a la izquierda */
    margin-left: -8rem;
    margin-top: -5rem;
}

.image-container {
    position: relative;
    width: 100%;
    max-width: 450px;
    animation: fadeInRight 0.8s ease-out 0.2s both;
}

@keyframes fadeInRight {
    from {
        opacity: 0;
        transform: translateX(30px);
    }
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

.profile-image {
    width: 100%;
    height: auto;
    border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
    box-shadow: 0 20px 40px rgba(0,0,0,0.1);
    transition: all 0.3s ease;
    position: relative;
    z-index: 6;
}

.profile-image:hover {
    transform: scale(1.02);
    border-radius: 40% 60% 60% 40% / 40% 40% 60% 60%;
}

.decorative-shape {
    position: absolute;
    bottom: -30px;
    left: 50%;
    transform: translateX(-50%);
    width: 80%;
    height: 85%;
    background: linear-gradient(135deg, var(--accent-red), #b91c5c);
    border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%;
    z-index: 4;
    opacity: 0.8;
    animation: float 6s ease-in-out infinite;
}

@keyframes float {
    0%, 100% {
        transform: translateX(-50%) translateY(0px) rotate(0deg);
    }
    50% {
        transform: translateX(-50%) translateY(-10px) rotate(2deg);
    }
}

/* Elementos flotantes decorativos */
.floating-elements {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    z-index: 7;
}

.dot {
    position: absolute;
    width: 12px;
    height: 12px;
    background: var(--accent-red);
    border-radius: 50%;
    animation: floatDot 4s ease-in-out infinite;
}

.dot-1 {
    top: 20%;
    left: 10%;
    animation-delay: 0s;
}

.dot-2 {
    top: 60%;
    right: 15%;
    width: 8px;
    height: 8px;
    animation-delay: 1.5s;
}

.dot-3 {
    bottom: 30%;
    left: 20%;
    width: 6px;
    height: 6px;
    background: var(--color3);
    animation-delay: 3s;
}

@keyframes floatDot {
    0%, 100% {
        transform: translateY(0px);
        opacity: 0.7;
    }
    50% {
        transform: translateY(-15px);
        opacity: 1;
    }
}

/* Círculo "Hire Me" mejorado */
.hire-me-circle-wrapper {
    position: absolute;
    top: 4rem;
    right: 4rem;
    width: 140px;
    height: 140px;
    background: var(--color1);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 15;
    cursor: pointer;
    transition: all 0.3s ease;
    animation: rotateWrapper 20s linear infinite;
}

.hire-me-circle-wrapper:hover {
    transform: scale(1.1);
    box-shadow: 0 8px 25px rgba(147, 20, 73, 0.4);
}

.hire-me-circle-wrapper:focus {
    outline: 2px solid var(--accent-red);
    outline-offset: 4px;
}

.circular-text-svg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

.inner-circle {
    position: relative;
    width: 70px;
    height: 70px;
    background: linear-gradient(135deg, var(--accent-red), #b91c5c);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 2;
    transition: all 0.3s ease;
}


@keyframes rotateWrapper {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
}

/* Elementos de fondo mejorados */
.background-grid {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: radial-gradient(circle at 1px 1px, rgba(0,0,0,0.05) 1px, transparent 0);
    background-size: 30px 30px;
    z-index: 0;
}

.background-blur-1, .background-blur-2 {
    position: absolute;
    border-radius: 50%;
    filter: blur(100px);
    z-index: 0;
    opacity: 0.1;
}

.background-blur-1 {
    top: 20%;
    left: 10%;
    width: 300px;
    height: 300px;
    background: var(--accent-red);
}

.background-blur-2 {
    bottom: 20%;
    right: 10%;
    width: 200px;
    height: 200px;
    background: var(--color3);
}

/* --- RESPONSIVE DESIGN --- */

/* Tablet */
@media (max-width: 1024px) {
    .hero-section {
        grid-template-columns: 1fr;
        gap: 3rem;
        padding: 2rem 3rem;
        text-align: center;
    }
    
    .content-wrapper {
        max-width: 100%;
    }
    
    /* MODIFICACIÓN 5: Reseteo los márgenes en tablet para mantener el centrado */
    .image-wrapper {
        justify-content: center;
        align-items: center;
        margin-left: 0;
        margin-top: 0;
    }
    
    .hire-me-circle-wrapper {
        top: 2rem;
        right: 2rem;
        width: 120px;
        height: 120px;
    }
    
    .inner-circle {
        width: 60px;
        height: 60px;
    }
}

/* Mobile */
@media (max-width: 768px) {
    .hero-section {
        padding: 1.5rem;
        gap: 2rem;
        min-height: auto;
    }

    .content-wrapper {
        order: 2;
    }

    .image-wrapper {
        order: 1;
        /* MODIFICACIÓN 6: También reseteo los márgenes en mobile */
        justify-content: center;
        align-items: center;
        margin-left: 0;
        margin-top: 0;
    }

    .title {
        font-size: clamp(2.5rem, 8vw, 4rem);
        margin-bottom: 1rem;
    }


    .buttons-container {
        flex-direction: column;
        align-items: center;
        gap: 1rem;
    }

    .btn {
        width: 100%;
        max-width: 280px;
        padding: 1rem 2rem;
    }

    .image-container {
        max-width: 350px;
    }

    .decorative-shape {
        width: 90%;
        height: 80%;
        bottom: -20px;
    }

    .hire-me-circle-wrapper {
        position: static;
        margin: 2rem auto 0;
        width: 100px;
        height: 100px;
    }

    .circular-text-svg text {
        font-size: 6px;
    }

    .inner-circle {
        width: 50px;
        height: 50px;
    }

    .floating-elements .dot {
        display: none;
    }
}

/* Mobile pequeño */
@media (max-width: 480px) {
    .hero-section {
        padding: 1rem;
        margin-left: -25px;
    }

    .title {
        font-size: 2.2rem;
        margin-left: 9.5rem;
    }

    .greeting {
        font-size: 1rem;
        margin-left: 6rem;
    }

    .image-container {
        max-width: 280px;
    }

    
    .buttons-container {
        flex-direction: column;
        align-items: left;
        gap: 1rem;
        margin-left: 100px;
    }

    .btn {
        width: 100%;
        max-width: 280px;
        padding: 1rem 2rem;
    }
    
}

/* Landscape mobile */
@media (max-height: 600px) and (orientation: landscape) {
    .hero-section {
        grid-template-columns: 1fr 1fr;
        min-height: 100vh;
        padding: 1rem 2rem;
    }
    
    .content-wrapper {
        order: 1;
    }
    
    .image-wrapper {
        order: 2;
        /* MODIFICACIÓN 7: Reseteo los márgenes también en landscape mobile */
        justify-content: center;
        align-items: center;
        margin-left: 0;
        margin-top: 0;
    }
    
    .hire-me-circle-wrapper {
        position: absolute;
        top: 1rem;
        right: 1rem;
        width: 80px;
        height: 80px;
    }
}
</style>