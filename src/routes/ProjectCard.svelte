<script>
    export let index;
    export let name;
    export let tools;
    export let collaborators;
    export let description;
    export let images;
    export let open = false;
    let hovering = false;
    import ChevronDown from "../lib/images//chevron-down.svg";

    import { slide } from "svelte/transition";
    import { linear } from "svelte/easing";

    const handleClick = () => (open = !open);
    const stopPropagation = (event) => {
        event.stopPropagation();
    };
</script>

<div
    on:click={handleClick}
    on:keydown={handleClick}
    role="switch"
    tabindex="0"
    aria-checked={open}
    class="p-3 mb-5 card project-card bg-dark"
    class:zindex-modal={open}
>
    <div class="row image-row">
        <h1 class="mt-1">{name}</h1>
        {#each tools as tool}
            <div
                class="col mx-5 px-0 mt-auto text-center"
                class:image-col-shrink={open}
                class:image-col={!open}
            >
                <img
                    class="img-fluid custom-img"
                    src={tool.icon}
                    alt={`${tool.name} icon`}
                />
                {#if !open}<p class="tool-name mx-0">{tool.name}</p>{/if}
            </div>
        {/each}
        <div class="chevron">
            {#if !open}
                <img src={ChevronDown} alt="" />
            {/if}
        </div>
    </div>
    {#if open}
        <div class="" transition:slide={{ duration: 200, easing: linear }}>
            <hr />
            <p class="mx-3">
                Collaborators:
                {collaborators}
            </p>
            <hr />

            <div class="row">
                <div class="mx-3 col">
                    <p class="description">
                        {@html description}
                    </p>
                </div>
                <div class="col">
                    <div
                        id="carouselExampleIndicators{index}"
                        class="carousel demo-images p-3 slide"
                        data-ride="carousel"
                    >
                        <ol class="carousel-indicators">
                            {#each images as _, idx}
                                <li
                                    data-bs-target="#carouselExampleIndicators{index}"
                                    data-bs-slide-to={idx}
                                    class={idx === 0 ? "active" : ""}
                                ></li>
                            {/each}
                        </ol>
                        <div class="carousel-inner">
                            {#each images as image, idx}
                                <div
                                    class="{idx === 0
                                        ? 'active'
                                        : ''} carousel-item"
                                >
                                    <img
                                        class="d-block w-100 carousel-image"
                                        src={image}
                                        alt={`Slide ` + idx}
                                        on:click={stopPropagation}
                                    />
                                </div>
                            {/each}
                        </div>
                        <a
                            class="carousel-control-prev"
                            href="#carouselExampleIndicators{index}"
                            role="button"
                            data-bs-slide="prev"
                            on:click={stopPropagation}
                        >
                            <span
                                class="carousel-control-prev-icon"
                                aria-hidden="true"
                            ></span>
                        </a>

                        <a
                            class="carousel-control-next"
                            href="#carouselExampleIndicators{index}"
                            role="button"
                            data-bs-slide="next"
                            on:click={stopPropagation}
                        >
                            <span
                                class="carousel-control-next-icon"
                                aria-hidden="true"
                            ></span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    {/if}
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Exo:wght@400;700&family=Work+Sans:wght@400;700&display=swap");

    h1 {
        font-family: "Exo", sans-serif;
        font-weight: 400; /* Adjust weight as needed */
    }

    p {
        font-family: "Work Sans", sans-serif;
        font-weight: 400; /* Adjust weight as needed */
    }
    .chevron {
        position: absolute;
        top: 40%;
        right: 7%;
        color: white;
        fill: white;
        fill: white;
        width: 1px;
    }
    .chevron img {
        width: 48px;
    }
    .project-card .chevron {
        transition: filter 0.3s ease; /* Smooth transition for the filter effect */
    }

    .project-card:hover .chevron {
        filter: invert(1) brightness(2); /* Invert the colors and increase brightness */
    }
    .demo-images {
        /* Set a static size for the carousel container */
        width: 100%;
        max-width: 600px; /* Adjust as needed */
        height: 450px; /* Adjust as needed */
    }
    .carousel-image {
        width: 100%;
        height: 100%;
        object-fit: cover; /* Ensure images cover the carousel container without distortion */
    }
    .carousel-inner {
        width: 100%;
        height: 100%;
    }

    .carousel-item {
        width: 100%;
        height: 100%;
    }
    .project-card {
        z-index: 1000;
        width: 60%;
        max-height: 100%;
        overflow-y: auto; /* Add scroll if content overflows */
        overflow-x: hidden;
        border: none;
    }
    hr {
        color: white;
    }
    h1,
    p {
        color: white;
    }

    .description {
        font-size: larger;
    }
    .image-col {
        transition-duration: 200ms;
        max-width: 100px; /* Set a maximum width for the images */
    }
    div.image-col-shrink {
        transition-duration: 200ms;
        max-width: 40px;
    }
    .demo-images {
        justify-content: center;
        align-items: center;
        text-align: center;
    }
    .custom-img {
        width: 100%;
        height: auto;
    }

    .tool-name {
        white-space: nowrap;
    }
    .image-row {
        justify-content: center;
    }
</style>
