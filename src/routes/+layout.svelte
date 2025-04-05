<script>
    import "./layout.scss";
</script>

<header>
    <img src="src\imgs\logo_svgbranco.svg" alt="Logo">
    <nav>
        <a href="/about">About</a>
        <a href="/docs">Documents</a>
        <a href="/projects">Projects</a>
        <div class="languages"></div>
        <div class="languages"></div>
    </nav>
</header>
<div id="sep"></div>
<slot></slot>
<footer>
    <p>teste</p>
</footer>