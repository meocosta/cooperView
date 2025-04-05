<script lang="ts">
    import "./page.scss";
    import * as Prism from "prismjs";
    import "prismjs/components/prism-typescript";
    import "prismjs/themes/prism-tomorrow.css";
    import { onMount } from "svelte";

    let classBar = "";
    let codeSnippet = `import * from std.io

func void main() {
    name = input!("What's your name?")

    println!("Your name is $name")
}`;
    let changing = true;

    onMount(() => {
        Prism.highlightAll();
    });

    var options = [
        {
            id: 0,
            title: "Easy",
            text: "Copper is easy to learn and use, it's syntax is simple and intuitive.",
        },
        {
            id: 1,
            title: "Fast",
            text: "Copper is a compiled language, so it's very fast.",
        },
        {
            id: 2,
            title: "Versatile",
            text: "Copper can be used for many things, from web development to system programming.",
        },
    ];

    let optionIndex = 0;

    if (changing) {
        setInterval(() => {
            changeOption(optionIndex);
            optionIndex = optionIndex == 2 ? 0 : optionIndex + 1;
        }, 5000);
    }

    $: if(!changing){
        console.log(changing);
        setTimeout(() => {
            changing = true;
        }, 5000);
    }

    var option = {
        id: options[optionIndex].id,
        title: options[optionIndex].title,
        text: options[optionIndex].text,
    };

    const changeOption = (tipo: number) => {
        option = {
            id: options[tipo].id,
            title: options[tipo].title,
            text: options[tipo].text,
        };
        switch (tipo) {
            case 0:
                classBar = "";
                break;

            case 1:
                classBar = "center";
                break;

            case 2:
                classBar = "right";
                break;
            default:
                break;
        }
    };

    $: console.log(option);
</script>

<section id="first">
    <div id="code">
        <div id="deco"></div>
        <div id="copper">
            <pre><code class="language-ts">{codeSnippet}</code></pre>
        </div>
    </div>
    <div id="titulo">
        <p>Stop using directly rust, instead use</p>
        <h1>Copper</h1>
    </div>
</section>

<section id="qualidades">
    <div id="options">
        <button
            class="option"
            on:click={() => {changeOption(0); changing = false}}
            style="color: {option.title == 'Easy' ? 'white' : '#d9d9d9'}"
            >Easy</button
        >
        <button
            class="option"
            on:click={() => {changeOption(1); changing = false}}
            style="color: {option.title == 'Fast' ? 'white' : '#d9d9d9'}"
            >Fast</button
        >
        <button
            class="option"
            on:click={() => {changeOption(2); changing = false}}
            style="color: {option.title == 'Versatile' ? 'white' : '#d9d9d9'}"
            >Versatile</button
        >
    </div>
    <div id="barrinha-container" class={classBar}>
        <div><hr id="barrinha" /></div>
    </div>
    <div id="content_qualidades">
        <h1>{option.title}</h1>
        <p>{option.text}</p>
    </div>
</section>

<section></section>
