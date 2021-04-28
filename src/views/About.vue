<template>
    <div id="about">
        <header>
            <a href="#" class="logo">lucky</a>
            <ul>
                <li><a href="#" class="active">Home</a></li>
                <li><a href="#">About</a></li>
                <li><a href="#">Work</a></li>
                <li><a href="#">Contact</a></li>
            </ul>
        </header>
        <section>
            <img src="../assets/stars.png" class="stars">
            <img src="../assets/moon.png" class="moon">
            <div class="desc">HELLO WORD!</div>
            <img src="../assets/mountains_behind.png" class="mountains_behind">
            <img src="../assets/mountains_front.png" class="mountains_front">
        </section>
        <div class="footer_text">
        <h2 class="footer_h2">《You Have Only One Life》</h2>
        <p class="footer_content">There are moments in life when you miss someone so much that you just want to pick them from your dreams and hug them for real! Dream what you want to dream;go where you want to go;be what you want to be,because you have only one life and one
            chance to do all the things you want to do.<br/><br/> May you have enough happiness to make you sweet,enough trials to make you strong,enough sorrow to keep you human,enough hope to make you happy? Always put yourself in others’shoes.If you
            feel that it hurts you,it probably hurts the other person, too.<br/><br/> The happiest of people don’t necessarily have the best of everything;they just make the most of everything that comes along their way.Happiness lies for those who cry,those
            who hurt, those who have searched,and those who have tried,for only they can appreciate the importance of people.<br/><br/>who have touched their lives.Love begins with a smile,grows with a kiss and ends with a tear.The brightest future will
            always be based on a forgotten past, you can’t go on well in lifeuntil you let go of your past failures and heartaches.When you were born,you were crying and everyone around you was smiling.Live your life so that when you die,you're the one
            who is smiling and everyone around you is crying.<br/><br/>Please send this message to those people who mean something to you,to those who have touched your life in one way or another,to those who make you smile when you really need it,to
            those that make you see the brighter side of things when you are really down,to those who you want to let them know that you appreciate their friendship.And if you don’t, don’t worry,nothing bad will happen to you,you will just miss out on
            the opportunity to brighten someone’s day with this message.<br>
        </p>
    </div>
    </div>
</template>
<script>
export default {
    data () {
        return {
            timeOut: null
        }
    },
    mounted () {
        const stars = document.querySelector('.stars');
        const moon = document.querySelector('.moon');
        const desc = document.querySelector('.desc');
        const mountains_behind = document.querySelector('.mountains_behind');
        const that = this
        window.addEventListener('scroll', function() {
            let value = window.scrollY;
            stars.style.left = value * 0.25 + 'px';
            moon.style.top = value * 1.05 + 'px';
            mountains_behind.style.top = value * 0.5 + 'px';
            desc.style.marginTop = value * 1.5 + "px";
            desc.style.right = value * 2.5 + "px";
        })
        that.moveDom()
    },
    methods: {
        moveDom () {
            const footer_h2 = document.querySelector('.footer_h2')
            const footer_content = document.querySelector('.footer_content')
            const max = footer_h2.offsetLeft + footer_content.offsetWidth - footer_h2.offsetWidth
            let leftMargin = footer_h2.offsetLeft
            let domTime = setInterval(() => {
                leftMargin += 10
                if (leftMargin > max) {
                    leftMargin = max
                    clearInterval(domTime)
                }
                footer_h2.style.left = leftMargin + 'px'
            }, 100)
        }
    }
}
</script>
<style scoped>
#about {
    min-height: 100vh;
    background: linear-gradient(#2b1055, #7597de);
    scroll-behavior: smooth;
}
header {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 10;
    padding: 20px 100px;
    box-sizing: border-box;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
header .logo {
    font-size: 20px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 2px;
    text-decoration: none;
    color: #fff;
}
header ul {
    list-style: none;
    display: flex;
    justify-content: center;
    align-items: center;
}
header ul li a {
    font-weight: 600;
    margin-left: 15px;
    transition: all .5s linear;
    padding: 5px 15px;
    border-radius: 20px;
    color: #fff;
    text-decoration: none;
}
header ul li a.active,
header ul li a:hover {
    background: #fff;
    color: #2b1055;
}
section {
    position: relative;
    width: 100%;
    overflow: hidden;
    height: 100vh;
    color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
}
section .desc {
    z-index: 5;
    font-size: 20px;
    font-weight: 700;
    position: absolute;
    right: -350px;
}
section::after {
    content: '';
    display: block;
    position: absolute;
    width: 100%;
    height: 100px;
    bottom: 0;
    left: 0;
    background: linear-gradient(to top, #1c0522, transparent);
    z-index: 7;
}
section img {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    object-fit: cover;
    pointer-events: none;
}
.stars {
    z-index: 1;
}
.moon {
    z-index: 2;
    mix-blend-mode: screen;
}
.mountains_behind {
    z-index: 4;
}
.mountains_front {
    z-index: 5;
}
.footer_text {
    color: #fff;
    background-color: #1c0522;
    height: 100vh;
    position: relative;
    padding: 20px;
}
.footer_h2 {
    position: absolute;
    left: 150px;
    font-size: 30px;
    font-weight: 600;
    overflow: hidden;
    top: 20px;
}
.footer_content {
    width: 80%;
    margin: 60px auto 0px;
}
</style>