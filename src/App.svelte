<script>
  let dark = false;
  let age = "X";

  function updateAge() {
    age = (
      new Date(new Date() - new Date("04/02/1998")) /
      (1000 * 60 * 60 * 24) /
      365
    ).toFixed(9);
  }
  setInterval(updateAge, 16);

  if (localStorage.getItem("darkPreferred") != null) {
    if (localStorage.getItem("darkPreferred") == "true") {
      dark = true;
    }
  } else if (
    window.matchMedia &&
    window.matchMedia("(prefers-color-scheme: dark)").matches
  ) {
    dark = true;
  }

  if (dark) {
    window.document.body.classList.add("dark-theme");
  }

  function toggleDark() {
    window.document.body.classList.add("transitionColorScheme");
    window.document.body.classList.toggle("dark-theme");
    dark = window.document.body.classList.contains("dark-theme");
    localStorage.setItem("darkPreferred", dark);
  }
</script>

<main>
  <div class="toggleHolder">
    <div class="buttonDiv" on:click={toggleDark}>
      {#if dark}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="100%"
          height="100%"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="feather feather-moon"
          ><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" /></svg
        >
      {:else}
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="100%"
          height="100%"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
          stroke-linecap="round"
          stroke-linejoin="round"
          class="feather feather-sun"
          ><circle cx="12" cy="12" r="5" /><line
            x1="12"
            y1="1"
            x2="12"
            y2="3"
          /><line x1="12" y1="21" x2="12" y2="23" /><line
            x1="4.22"
            y1="4.22"
            x2="5.64"
            y2="5.64"
          /><line x1="18.36" y1="18.36" x2="19.78" y2="19.78" /><line
            x1="1"
            y1="12"
            x2="3"
            y2="12"
          /><line x1="21" y1="12" x2="23" y2="12" /><line
            x1="4.22"
            y1="19.78"
            x2="5.64"
            y2="18.36"
          /><line x1="18.36" y1="5.64" x2="19.78" y2="4.22" /></svg
        >
      {/if}
    </div>
  </div>
  <h1>Hi, I am <span>Austin Merrick</span></h1>
  <p class="headerSubtext">
    I work as a software engineer and create projects in my free time. This
    website serves as a portfolio to showcase my projects and experience.
  </p>

  <h2>About.json</h2>
  <div class="code">
    {"{\n"}
    <p>"age": {age},</p>
    <p>"skills": ["software engineering", "design"],</p>
    <p>"hobbies": ["chess", "climbing", "piano"],</p>
    <p>"email": "austinmerrick98@gmail.com",</p>
    <p>"twitter": <a href="https://twitter.com/onsclom">"@onsclom"</a>,</p>
    <p>
      "inspirations": [<a href="https://100r.co/site/home.html"
        >"hundred rabbits"</a
      >,
      <a href="https://managore.itch.io/">"managore"</a>,
      <a href="http://ledoux.io/bitsy/editor.html">"bitsy"</a>,
      <a href="https://www.puzzlescript.net/">"puzzlescript"</a>,
      <a href="http://txti.es/">"txti"</a>,
      <a href="https://constraint.systems/">"constraint systems"</a>]
    </p>
    {"}"}
  </div>

  <div>
    <h2>Projects</h2>
  
    <div class="project">
      <h3>
        <a href="https://cegexe.itch.io/holymatrixmony">Holy Matri(x)mony</a>
      </h3>
      <p>
        A puzzle game made in 48 hours which ranked as a finalist in the GMTK 2021
        Game Jam. Made with Godot and GDScript.
      </p>
    </div>
  
    <div class="project">
      <h3>
        <a href="https://onsclom.github.io/blunder-chess/">Blunder Chess</a>
      </h3>
      <p>
        Chess puzzles where you have to find the worst possible move. Puzzles
        generated with Python. Front end made using vanilla JS, HTML, and CSS.
      </p>
    </div>
  
    <div class="project">
      <h3>
        <a href="https://projects-onsclom.vercel.app/">Svelte Projects</a>
      </h3>
      <p>
        A collection of projects I made to learn Svelte. Includes a quote machine,
        markdown previewer, drum machine, calculator, 25+5 timer, and a lifespan
        calculator.
      </p>
    </div>
  
    <div class="project">
      <h3>
        <a href="https://onsclom.github.io/spurts/">Spurts</a>
      </h3>
      <p>
        An anonymous message board. Backend built using Firebase, and frontend using vanilla JavaScript, HTML, and CSS.
      </p>
    </div>
  
    <div class="project">
      <h3>
        <a href="https://cegexe.itch.io/rotato-ship">Rotato Ship</a>
      </h3>
      <p>
        A rotating platformer made in 48 hours which ranked as a finalist in the GMTK 2020
        Game Jam. Made with Godot and GDScript.
      </p>
    </div>
  </div>

  <p>Website built by me using Svelte. View the messy code <a href="https://github.com/onsclom/personal-website">here</a>.</p>
</main>

<style>
  a {
    font-size: inherit;
    color: var(--primary-color);
    text-decoration: none;
    position: relative;
  }

  a::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 50%;
    width: 0%;
    border-bottom: 2px solid var(--primary-color);
    transition: all 0.4s ease;
  }

  a:hover::after {
    left: 0%;
    width: 100%;
  }

  h1 {
    margin-top: 0;
  }

  h1 span {
    /* -webkit-text-stroke: .5px var(--main-bg-color); */
    text-shadow: 4px 4px var(--light-shadow);
    white-space: nowrap;
  }

  .buttonDiv {
    display: inline-block;
    cursor: pointer;
    text-align: right;
    width: 2.5rem;
    height: 2.5rem;
    color: var(--strong-color);
  }

  .toggleHolder {
    text-align: right;
    margin-top: 1rem;
  }

  h2 {
    /* -webkit-text-stroke: .5px var(--main-bg-color); */
    /* text-shadow: 4px 4px var(--light-shadow); */
  }

  .project h3 {
    margin-bottom: 0;
  }
  main {
    transition: inherit;
    max-width: 40rem;
    box-sizing: border-box;
    padding: 0 min(2%,2rem);
    /* min-height: 100%; */
    margin: auto;
    color: var(--main-color);
    background-color: var(--main-bg-color);
  }
  .project {
    margin: 1rem;
    margin-bottom: 2rem;
    /* margin-left: 0; */
    padding-left: 1rem;
    border-left: 2px solid var(--main-color);
    /* padding: .5rem; */
    /* box-shadow: 4px 4px var(--main-color); */
  }

  .code {
    border: 2px solid var(--main-color);
    box-shadow: 4px 4px var(--main-color);
    padding: 0.5rem;
    margin: 1rem;
    overflow-x: auto;
    font-family: inherit;
    line-height: 1.5;
  }

  .code p {
    text-indent: 1rem;
    margin: 0.5rem 0;
    line-height: 1.5;
  }
</style>
