<style>
    h1 {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        margin: 0;
        animation: wave 1.5s infinite;
    }

    h2 {
        text-align: center;
        color: #111;
        position: absolute;
        top: 55%;
        left: 50%;
        transform: translateX(-50%);
    }

    a {
        color: #FF3E00;
    }

    @keyframes wave {
        0%   { transform: rotate(0) translate(-50%, -50%); }
        10%  { transform: rotate(-5deg) translate(-50%, -50%); }
        20%  { transform: rotate(10deg) translate(-50%, -50%); }
        30%  { transform: rotate(-5deg) translate(-50%, -50%); }
        40%  { transform: rotate(10deg) translate(-50%, -50%); }
        50%  { transform: rotate(0) translate(-50%, -50%); }
        100% { transform: rotate(0) translate(-50%, -50%); }
    }
</style>

<h1>👋</h1>
<h2>
    <p><img src="assets/svelte.png" alt="" style="width:50px;height:60px;"/></p>
    Welcome to <a href="https://svelte.dev/">Svelte</a>,<br />
    bundled by <a href="https://www.snowpack.dev/">Snowpack</a>
</h2>
