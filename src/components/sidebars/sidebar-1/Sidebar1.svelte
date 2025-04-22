<script>
  import logo from "./logo.svg";

  const navItems = [
    { icon: "home", name: "Home" },
    { icon: "leaderboard", name: "Leaderboard" },
    { icon: "favorite", name: "Liked" },
    { icon: "bookmark", name: "Saved" },
    { icon: "lock", name: "Account" },
  ];

  let active = 1;
</script>

<section class="page sidebar-page">
  <aside class="sidebar">
    <div class="inner">
      <div class="header">
        <img src={logo} class="logo" alt="logo" />
        <h1>Lampo</h1>
      </div>
      <nav class="menu" style={`--top: ${active === 0 ? 0 : active * 56}px`}>
        {#each navItems as item, index}
          <button
            onclick={() => (active = index)}
            type="button"
            class:active={index === active}
          >
            <span class="material-symbols-outlined">
              {item.icon}
            </span>
            <p>{item.name}</p>
          </button>
        {/each}
        <button style="margin-top: auto; padding-bottom: 20px;" type="button">
          <span class="material-symbols-outlined"> settings </span>
          <p>Settings</p>
        </button>
      </nav>
    </div>
  </aside>
</section>

<style>
  * {
    box-sizing: border-box;
  }

  .sidebar {
    --width-open: 260px;
    --width-closed: 64px;
  }

  .page.sidebar-page {
    margin: 0;
    height: 100vh;
    background: #95a9ee;
    color: #f9f9f9;
    font-family: "Euclid Circular A", "Poppins";
  }

  button {
    background: transparent;
    border: 0;
    padding: 0;
    cursor: pointer;
  }

  .sidebar {
    overflow: hidden;
    position: absolute;
    top: 20px;
    left: 20px;
    bottom: 20px;
    width: var(--width-closed);
    border-radius: 16px;
    background: #1f2435;
    transition: width 0.3s;
  }

  .sidebar:hover {
    width: var(--width-open);
  }

  .inner {
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    width: 260px;
    display: flex;
    flex-direction: column;
  }

  .header {
    display: flex;
    align-items: center;
    height: 72px;
    width: var(--width-closed);
    padding: 0 18px;
    background: rgb(0 0 0 / 5%);
    border-top-left-radius: 16px;
    border-top-right-radius: 16px;
    transition: 0.3s;
  }

  .sidebar:hover .header {
    width: var(--width-open);
  }

  .header h1 {
    margin-left: 12px;
    font-weight: 500;
    font-size: 16px;
    letter-spacing: 2px;
  }

  .logo {
    height: 28px;
  }

  .menu {
    position: relative;
    display: flex;
    flex-direction: column;
    flex: 1 1 auto;
  }

  .menu::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 56px;
    width: 6px;
    background: #4368e4;
    translate: 0 var(--top);
    transition: 0.3s;
  }

  .menu button {
    display: flex;
    gap: 16px;
    align-items: center;
    height: 56px;
    width: var(--width-closed);
    font-family: "Poppins";
    font-size: 16px;
    text-transform: capitalize;
    line-height: 1;
    padding: 0 22px;
    color: #afb3bf;
    cursor: pointer;
    opacity: 0.8;
    transition-property: background, width;
    transition-duration: 0.3s;
  }

  .menu button > span {
    font-size: 22px;
  }

  .sidebar:hover .menu button {
    width: var(--width-open);
  }

  .menu button.active {
    color: #f9f9f9;
    background: #2a3048;
    opacity: 1;
  }

  .menu button:not(.active):hover {
    background: #242940;
    opacity: 0.9;
  }

  .sidebar:hover .menu .active {
    cursor: default;
  }

  .menu button:hover > span {
    opacity: 1;
  }

  .menu button p,
  .header h1 {
    opacity: 0;
    transition: 0.3s;
  }

  .menu button:hover p {
    transition: 0.1s;
  }

  .sidebar:hover :is(.sidebar .menu button p, .sidebar .header h1) {
    opacity: 1;
  }
</style>
