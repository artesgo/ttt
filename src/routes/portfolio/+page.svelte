<!-- fancy styles page -->
<!-- 
    demonstrate some of the stuff that
    we learn about html css 
    javascript
-->
<h1>Portfolio Page</h1>

<div class="portfolio">
    <div class="flex-row">
        <div class="cut-off">
            <img width="300px" src="./photo-1572985025058-f27aeca1b8bf.avif" alt="" />
            <h2>css</h2>
        </div>
        <ul>
            <li>style elements via class</li>
            <li>css properties like display, border, margins, etc</li>
        </ul>
    </div>
    <div class="flex-row">
        <div class="cut-off">
            <img width="300px" src="./photo-starbucks.avif" alt="" />
            <h2>javascript</h2>
        </div>
        <ul>
            <li>functions are pieces of code that we can run over and over again</li>
            <li>parameters are part of the function signature that the function uses</li>
        </ul>
    </div>
    <div class="flex-row">
        <div class="cut-off">
            <img width="300px" src="./premium_html.avif" alt="" />
            <h2>html</h2>
        </div>
        <ul>
            <li>the basic structure of the web page</li>
            <li>it contains the elements that we use to build the web</li>
        </ul>
    </div>
</div>

<style>
    .portfolio {
        display: flex;
        justify-content: space-around;
    }

    .flex-row {
        display: flex;
        flex-direction: column;
    }

    .cut-off {
        height: 175px;
        overflow: hidden;
        position: relative;
    }

    h2 {
        position: absolute;
        top: 10px;
        left: 10px;
        color: white;
    }

    li {
        width: 300px; 
    }

    ul {
        list-style: circle;
    }
</style>