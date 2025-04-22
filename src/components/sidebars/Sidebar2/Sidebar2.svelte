<script>
  import logo from "./logo.svg";

  const navItems = [
    "home-2",
    "envelope-1",
    "calendar-days",
    "colour-palette-3",
    "heart",
  ];

  let isOpen = false;
</script>

<section class="page sidebar-page">
  <button
    aria-label="burger"
    type="button"
    class="burger"
    onclick={() => (isOpen = !isOpen)}
  >
    <i class="lni lni-menu-hamburger-1"></i>
  </button>
  <aside class={`sidebar ${isOpen ? "open" : ""}`}>
    <div class="inner">
      <header>
        <img src={logo} alt="logo" />
      </header>
      <nav>
        {#each navItems as item}
          <button type="button">
            <span class={`lni lni-${item}`}></span>
            <p>{item}</p>
          </button>
        {/each}
        <button aria-label="settings" type="button">
          <i class="lni lni-gear-1"></i>
        </button>
      </nav>
    </div>
  </aside>
</section>

<style>
  .page.sidebar-page {
    height: 100vh;
    background: #413e45;
  }

  .page.sidebar-page button {
    background: transparent;
    border: 0;
    cursor: pointer;
  }

  .sidebar {
    position: absolute;
    z-index: 1;
    top: 0;
    left: 0;
    bottom: 0;
    width: 56px;
    background: #141417;
    backdrop-filter: blur(10px);
    transition: 0.45s;
  }

  .sidebar .material-symbols-outlined {
    font-size: 20px;
  }

  .sidebar.open {
    width: 190px;
    overflow: hidden;
  }

  .sidebar .inner {
    position: absolute;
    top: 0;
    left: 0;
    width: 190px;
    height: 100%;
    display: flex;
    flex-direction: column;
  }

  .sidebar header {
    display: flex;
    align-items: center;
    height: 64px;
    padding: 0 6px 0 48px;
  }

  .burger {
    position: fixed;
    z-index: 2;
    top: 0;
    left: 0;
    width: 56px;
    height: 64px;
    display: grid;
    place-items: center;
    color: #f9f9f9;
  }

  .sidebar header > img {
    height: 18px;
  }

  .sidebar nav {
    display: flex;
    flex-direction: column;
    padding: 0 8px 20px;
    gap: 2px;
    flex: 1 1 auto;
  }

  .sidebar nav > button {
    display: flex;
    gap: 12px;
    align-items: center;
    height: 40px;
    width: 40px;
    font-family: "Poppins";
    font-size: 14px;
    text-transform: capitalize;
    line-height: 1;
    padding: 0 10px;
    border-radius: 8px;
    color: #f9f9f9;
  }

  .lni {
    display: grid;
    place-items: center;
    font-size: 20px;
  }

  .sidebar nav > button:last-child {
    margin-top: auto;
  }

  .sidebar nav > button:hover {
    background: #8f44fd;
  }

  .sidebar:not(.open) nav p {
    white-space: nowrap;
    visibility: hidden;
  }

  .sidebar:not(.open) nav > button:hover p {
    opacity: 1;
    visibility: visible;
    background: #47434e;
    padding: 5px 10px;
    font-size: 13px;
    border-radius: 6px;
    translate: 12px 0;
  }

  .sidebar header > img,
  .sidebar nav > button p {
    opacity: 0;
    transition: 0.25s;
  }

  .sidebar.open :is(nav button p, header > img) {
    opacity: 1;
  }

  .sidebar.open nav > button {
    width: 100%;
  }

  @media (width <= 400px) {
    .sidebar {
      translate: -100% 0;
    }

    .sidebar.open {
      translate: 0;
    }

    .sidebar:not(.open) button span {
      transition: 0.3s;
      opacity: 0;
    }
  }
</style>
