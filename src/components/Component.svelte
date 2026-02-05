<script>
    import { onMount } from "svelte";
    import { gsap } from 'gsap/dist/gsap.js';
    // For plugins, e.g., ScrollTrigger
    import { ScrollTrigger } from 'gsap/dist/ScrollTrigger.js';
    

    if (typeof window !== "undefined") {
        gsap.registerPlugin(ScrollTrigger);
    }

    let component;
    let content;
    let slider

    onMount(() => {
        
    const ctx = gsap.context((self) => {
        gsap.to(slider, {
            scrollTrigger: {
                trigger: component,
                start: "top top",
                end:  "bottom+=200px 75%",
                scrub: 1,
                pin: component,
                invalidateOnRefresh: true,
            },
            x: () => 0 - (slider.offsetWidth - window.innerWidth),
            duration: 5
        });

            console.log("x: ",0 - (slider.offsetWidth - window.innerWidth));
            console.log('slider offset width: ', slider.offsetWidth);
            console.log('window inner width: ',window.innerWidth);


    }, component); // <- Scope!


    return () => ctx.revert(); // <- Cleanup!
  });


</script>

<div class="component bg-color" bind:this={component}>
    <div class="component-content" bind:this={content}>
        <section>
            <p class="button">CTA Button Name</p>
            <h1>At massa feugiat mauris diam</h1>
            <h2>Gmassa nisl malesuada lacinia integer nunc posuere ut hendrerit</h2>
        </section>

        <div class="carousel-container">
            <div class="slider" bind:this={slider}>
                <div class="slider-margin"></div>
            
                <div class="card">
                    <p class="number">01</p>
                    <div class="card-details">
                        <h3>Neque risus maecenas</h3>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                    </div>
                    
                </div>

                <div class="card">
                    <p class="number">02</p>
                    <div class="card-details">
                        <h3>Posuere leo eu nisl at tellus</h3>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                    </div>
                    
                </div>

                <div class="card">
                    <p class="number">03</p>
                    <div class="card-details">
                        <h3>Nisl tempor eu tortor vel est dictum</h3>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                    </div>
                    
                </div>

                <div class="card last-card">
                    <p class="number">04</p>
                    <div class="card-details">
                        <h3>Duis aute irure dolor in reprehenderit</h3>
                        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                    </div>
                    
                </div>

                <div class="slider-margin"></div>
            
            </div>
        </div>
    </div>
    
    
</div>

<style>

:root{
    --slider-margin: 10vw;
    --carousel-padding: 40px;
    --slider-blur: 10px;
    --card-width: 80vw;
    --card-height: 300px;
    --slider-gap: 2vw;
}

@media (min-width: 600px) {
  :root{
    --card-width: 25vw;
    --card-height: 250px;
  }
}

@media (min-width: 1000px) {
  :root{
    --slider-gap: 1vw;
    --card-width: 26vw;
    --card-height: 250px;
  }
}
.component{
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    z-index: 3;
    position: relative;
}


.bg-color{
    background-color: var(--maincolor);
}

section{
    text-align: center;
}

.carousel-container{
    overflow: hidden;
    width: 100vw;
    height: var(--card-height);
    margin: var(--spacing5) 0px;
}

.carousel-container::before{
    content: '';
    height: inherit;
    width: var(--slider-margin);
    position: absolute;
    z-index: 1;
    padding: var(--carousel-padding) 0px;
    transform: translateY(calc( 0px - var(--carousel-padding)));
    backdrop-filter: blur(var(--slider-blur));
    /* Standard property */
    mask-image: linear-gradient(to right, black, transparent);
    /* Webkit prefix for broader compatibility (still needed for some browsers) */
    -webkit-mask-image: linear-gradient(to right, black, transparent); 
}

.carousel-container::after{
    content: '';
    height: inherit;
    width: var(--slider-margin);
    position: absolute;
    z-index: 1;
    padding: var(--carousel-padding) 0px;
    transform: translateY(calc( 0px - var(--carousel-padding)));
    right: 0;
    backdrop-filter: blur(var(--slider-blur));
    /* Standard property */
    mask-image: linear-gradient(to left, black, transparent);
    /* Webkit prefix for broader compatibility (still needed for some browsers) */
    -webkit-mask-image: linear-gradient(to left, black, transparent); 
}

/* Hide scrollbar for Chrome, Safari and Opera */
.carousel-container::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.carousel-container {
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

.slider{
    display: flex;
    position: absolute;
    height: inherit;
}

.slider > * {
    flex-shrink: 0;
}


.card{
    background-color: white;
    padding: var(--spacing3);
    margin-right: var(--slider-gap);
    border-radius: var(--spacing3);
    display: flex;
    flex-direction: column;
    gap: var(--spacing1);
    color: black;
    height: auto;
    width: var(--card-width);
    justify-content: space-between;
}

.last-card{
    margin-right: 0;
}

.slider-margin{
    width: var(--slider-margin);
    height: inherit;
}

.button{
    font-weight: 600;
    border: 1px solid white;
    padding: var(--spacing2) var(--spacing3);
    border-radius: var(--spacing6);
    transition: all 0.5s ease;
    width: fit-content;
    margin: auto;
    
}

.button:hover{
    background-color: rgb(236, 236, 236);
    box-shadow: inset 0px 1px 1px 1px white, 0px 2px 7px 0px rgba(0, 0, 0, 0.5);
    border: 1px solid rgb(202 200 200);
    color: var(--maincolor);
    transform: scale(1.1);
}

.card-details > p{
    color: gray;
}


</style>