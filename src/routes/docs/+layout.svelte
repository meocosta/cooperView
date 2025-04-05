<script lang="ts">
    import "./docs.scss";

    let active = "/docs";

    const change = (open : Boolean) =>{
        const aside = document.querySelector('aside') as HTMLElement;
        const conteudo = document.querySelector('#conteudo') as HTMLElement;
        if(open && aside != undefined && conteudo != undefined){ 
            conteudo.style.width = '80vw';
            aside.style.width = '20vw';
        }else{
            aside.style.width = '10vw';
            conteudo.style.width = '90vw';
        }
    }
</script>

<section id="docs">
    <aside onmouseenter="{() => {change(true)}}" onmouseleave="{() => {change(false)}}">
        <a
            href="/docs"
            onclick={() => {
                active = "/docs";
            }}
            style="color: {active === '/docs' ? 'white' : 'gray'}"
        >
            Intro
        </a>
        <a
            href="/docs/types"
            onclick={() => {
                active = "/types";
            }}
            style="color: {active === '/types' ? 'white' : 'gray'}"
        >
            Types
        </a>
    </aside>
    <section id="conteudo">
        <slot></slot>
    </section>
</section>
