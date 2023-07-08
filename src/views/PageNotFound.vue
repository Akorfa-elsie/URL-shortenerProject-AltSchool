<template>
    <div class="error-page">
        <div>
            <h1>Error 404</h1>
            <p>Sorry, this page does not exist.</p>
        </div>
        <div>
            <p>Click to go back to the home page.</p>
            <router-link to="/"><button className='counter-btn'>
                   Back to Homepage
                </button></router-link>
        </div>
    </div>
</template>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;

    font-family: 'Open Sans', sans-serif;
    background-color: #16161a;
}
.error-page {
    max-width: 600px;
    margin: auto;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
}

.counter-btn {
    background-color: pink;
    color: brown;
    margin: 5px;
    padding: 10px 15px;
    border: none;
    border-radius: 10px;
}

h1 {
    color: #fffffe;
}

p {
    color: #94a1b2
}
</style>