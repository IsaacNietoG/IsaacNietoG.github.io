---
layout: default
title: Inicio
---

<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ site.title }} - Inicio</title>
    <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
</head>
<body>
    <section id="introduction">
        <h2>Bienvenido a mi portafolio</h2>
        <p>Soy un desarrollador apasionado por la tecnología y la seguridad informática. Aquí puedes explorar mis proyectos, leer mis artículos de blog, y aprender más sobre mí.</p>
    </section>

    <section id="featured-projects">
        <h2>Proyectos Destacados</h2>
        <div class="projects">
            <div class="project">
                <h3><a href="{{ '/portfolio/proyecto-1' | relative_url }}">Proyecto 1</a></h3>
                <p>Descripción breve del proyecto 1.</p>
            </div>
            <div class="project">
                <h3><a href="{{ '/portfolio/proyecto-2' | relative_url }}">Proyecto 2</a></h3>
                <p>Descripción breve del proyecto 2.</p>
            </div>
            <!-- Agrega más proyectos destacados aquí -->
        </div>
    </section>

    <section id="latest-posts">
        <h2>Últimos Artículos</h2>
        <ul>
            {% for post in site.posts limit:3 %}
                <li>
                    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
                    <p>{{ post.excerpt }}</p>
                    <p><small>{{ post.date | date: "%d %B, %Y" }}</small></p>
                </li>
            {% endfor %}
        </ul>
    </section>

</body>
</html>
