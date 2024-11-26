<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="name.css">
</head>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Aboreto&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
body{
    font-family: Poppins;
    margin: 0;
    font-size: 16px;
    background-color: #4f8b69;
}
*{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    text-decoration: none;
    list-style: none;
}
:root{
    --border-color: #fff5;
    --w-image: 500px;
    --calculate: calc(3 / 2);
}
header{
    display: grid;
    grid-template-columns: 80px 1fr calc(var(--w-image) * var(--calculate));
    grid-template-rows: 80px;
    position: relative;
    z-index: 10;
    border-bottom: 1px solid var(--border-color);
}
header .logo img{
    width: 80%;
}
header .logo{
    display: flex;
    justify-content: center;
    align-items: center;
}
header nav a{
    color: #000;
    font-weight: 400;
}
header nav ul{
    height: 100%;
    display: flex;
    justify-content: end;
    align-items: center;
    gap: 30px;
    padding-right: 30px;
}
header nav{
    border-left: 1px solid var(--border-color);
}
.carousel{
    margin-top: -80px;
    width: 100%;
    height: 100vh;
    overflow: hidden;
}
.carousel .list{
    height: 100%;
    position: relative;
}
.carousel .list::before{
    position: absolute;
    width: var(--w-image);
    height: 100%;
    content: '';
    top: 0;
    left: calc(100% - calc(var(--w-image) * var(--calculate)));
    border-left: 1px solid var(--border-color);
    border-right: 1px solid var(--border-color);
    z-index: 10;
    pointer-events: none;
}
.carousel .list::after{
    position: absolute;
    top: 50px;
    left: 50px;
    content: '';
    background-color: red;
    width: 400px;
    height: 300px;
    z-index: 10;
    pointer-events: none;
    border-radius: 20px  50px 110px  230px;
    filter: blur(150px);
    opacity: .6;
}
.carousel .list .item{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}
.carousel .list .item .image{
    width: var(--w-image);
    height: 100%;
    position: absolute;
    top: 0;
    left: calc(100% - calc(var(--w-image) * var(--calculate)));
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: end;
    align-items: center;
    font-weight: 500;
}
.carousel .list .item .image img{
    width: 90%;
    margin-bottom: 20px;
    filter: drop-shadow(0 150px 50px #9e0c0c55);
}
.carousel .list .item .image figcaption{
    font-family: 'Aboreto';
    font-weight: bold;
    font-size: 1.3em;
    text-align: right;
    margin-bottom: 30px;
    width: 70%;
}
.carousel .list .item .main-content{
    height: 100%;
    display: grid;
    grid-template-columns: calc(100% - calc(var(--w-image) * var(--calculate)));
}
.carousel .list .item .main-content .content{
    padding: 150px 20px  20px 80px;
}
.carousel .list .item .main-content .content h2{
    font-size: 5em;
    font-family: 'Aboreto';
}
.carousel .list .item .main-content .content .price{
    font-family: 'Aboreto';
    font-size: 3em;
    margin: 20px 0;
}
.carousel .list .item .main-content .content .addToCard{
    background-color: #4f8b69;
    color: #fff;
    padding: 10px  30px;
    font-family: Poppins;
    font-size: large;
    font-weight: 500;
    border-radius: 30px;
    border: none;
    margin-top: 20px;
}
.arrows{
    position: absolute;
    bottom: 20px;
    width: calc(100% - calc(var(--w-image) * var(--calculate)));
    display: grid;
    grid-template-columns: repeat(2, 50px);
    grid-template-rows: 50px;
    justify-content: end;
    gap: 10px;
}
.arrows button{
    background-color: transparent;
    border: 1px solid var(--border-color);
    color: #fff;
    font-family: monospace;
    font-size: large;
    font-weight: bold;
    line-height: 0;
    box-shadow: 0 10px 40px #5555;
    cursor: pointer;
    transition: 0.5s;
}
.arrows button:hover{
    background-color: #eee5;
}
.carousel .list .item{
    display: none;
}
.carousel .list .item.active,
.carousel .list .item.other_1,
.carousel .list .item.other_2{
    display: block;
}
.carousel .list .item.active{
    z-index: 2;
}
.carousel .list .item.other_1,
.carousel .list .item.other_2{
    pointer-events: none;
}
.carousel .list .item.active .main-content{
    animation: showContent 1s ease-in-out 1 forwards;
}
@keyframes showContent{
    from{
        clip-path: circle(0% at 70% 50%);
    }to{
        clip-path: circle(100% at 70% 50%);
    }
}
.next .item.other_1{
    z-index: 1;
}
.next .item .image img,
.next .item .image figcaption{
    animation: effectNext .5s ease-in-out 1 forwards;
}
@keyframes effectNext{
    from{
        transform: translateX(calc(var(--transform-from)));
    }to{
        transform: translateX(calc(var(--transform-from) - var(--w-image)));
    }
}
.next .item.active .image{
    --transform-from: var(--w-image);
}
.next .item.other_1 .image{
    z-index: 3;
    --transform-from: 0px;
    overflow: hidden;
}
.next .item.other_2 .image{
    z-index: 3;
    --transform-from: calc(var(--w-image) * 2);
}
.arrows{
    z-index: 10;
}
/* prev */
.prev .list .item .image img,
.prev .list .item .image figcaption{
    animation: effectPrev 0.5s ease-in-out 1 forwards;
}
@keyframes effectPrev{
    from{
        transform: translateX(calc(var(--transform-from)));
    }to{
        transform: translateX(calc(var(--transform-from) + var(--w-image)));
    }
}
.prev .list .item.active .image{
    --transform-from: calc(var(--w-image) * -1);
    overflow: hidden;
}
.prev .list .item.other_1 .image{
    --transform-from: 0px;
    z-index: 3;
}
.prev .list .item.other_2 .image{
    z-index: 3;
    --transform-from: var(--w-image);
}
.prev .list .item.other_2 .main-content{
    opacity: 0;
}
@media screen and (max-width: 1023px){
    :root{
        --calculate: 1;
        --w-image: 400px; 
    }
    .carousel .list .item .main-content .content h2{
        font-size: 3em;
    }
}
@media screen and (max-width: 767px){
    .carousel .list .item .image{
        width: 100%;
        left: 0;
        justify-content: center;
    }
    .carousel .list .item .image figcaption{
        color: #fff;
        width: 100%;
        text-align: center;
    }
    .carousel .list .item .main-content .content{
        display: none;
    }
    .arrows{
        left: 50%;
        justify-content: center;
    }
}
    </style>
<body>
    <header>
        <figure class="logo">
            <img src="logo.png" alt="">
        </figure>
        <nav class="main-nav">
            <ul>
                <li><a href="">Coffee</a></li>
                <li><a href="">Menu</a></li>
                <li><a href="">About</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section class="carousel next">
            <div class="list">
                <article class="item other_1">
                    <div class="main-content" 
                    style="background-color: #9c4d2f;">
                        <div class="content">
                            <h2>Caffe Latte, a new product</h2>
                            <p class="price">$ 20</p>
                            <p class="description">
                                Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores labore animi voluptatibus sequi illo, earum molestias explicabo officiis iste neque? Quis quod eligendi fugit, dolore nam itaque modi exercitationem voluptatem corrupti aut aspernatur. Quos non in sed ratione tenetur harum.
                            </p>
                            <button class="addToCard">
                                Add To Card
                            </button>
                        </div>
                    </div>
                    <figure class="image">
                        <img src="1.png" alt="">
                        <figcaption>Caffe Latte, a new product</figcaption>
                    </figure>
                </article>
                <article class="item active">
                    <div class="main-content" 
                    style="background-color: #f5bfaf;">
                        <div class="content">
                            <h2>Strawberry mocha, a new product</h2>
                            <p class="price">$ 20</p>
                            <p class="description">
                                Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores labore animi voluptatibus sequi illo, earum molestias explicabo officiis iste neque? Quis quod eligendi fugit, dolore nam itaque modi exercitationem voluptatem corrupti aut aspernatur. Quos non in sed ratione tenetur harum.
                            </p>
                            <button class="addToCard">
                                Add To Card
                            </button>
                        </div>
                    </div>
                    <figure class="image">
                        <img src="2.png" alt="">
                        <figcaption>Strawberry mocha, a new product</figcaption>
                    </figure>
                </article>
                <article class="item other_2">
                    <div class="main-content" 
                    style="background-color: #dedfe1;">
                        <div class="content">
                            <h2>Doppio espresso, a new product</h2>
                            <p class="price">$ 20</p>
                            <p class="description">
                                Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores labore animi voluptatibus sequi illo, earum molestias explicabo officiis iste neque? Quis quod eligendi fugit, dolore nam itaque modi exercitationem voluptatem corrupti aut aspernatur. Quos non in sed ratione tenetur harum.
                            </p>
                            <button class="addToCard">
                                Add To Card
                            </button>
                        </div>
                    </div>
                    <figure class="image">
                        <img src="3.png" alt="">
                        <figcaption>Doppio espresso, a new product</figcaption>
                    </figure>
                </article>
                <article class="item">
                    <div class="main-content" 
                    style="background-color: #7eb63d;">
                        <div class="content">
                            <h2>Matcha latte macchiato, a new product</h2>
                            <p class="price">$ 20</p>
                            <p class="description">
                                Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores labore animi voluptatibus sequi illo, earum molestias explicabo officiis iste neque? Quis quod eligendi fugit, dolore nam itaque modi exercitationem voluptatem corrupti aut aspernatur. Quos non in sed ratione tenetur harum.
                            </p>
                            <button class="addToCard">
                                Add To Card
                            </button>
                        </div>
                    </div>
                    <figure class="image">
                        <img src="4.png" alt="">
                        <figcaption>Matcha latte macchiato, a new product</figcaption>
                    </figure>
                </article>
            </div>
            <div class="arrows">
                <button id="prev"><</button>
                <button id="next">></button>
            </div>
        </section>
    </main>

    <script src="name.js"></script>
</body>
</html>
