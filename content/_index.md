+++
title = "Inicio" 
template = "index.html"
+++
# Hi! Welcome to my halls of reflection!
![Yo](/assets/images/me.jpg)

Hi! I'm Isaac (Tchai pa los amigos), a third semester Computer Science student with a passion for technology, programming, music, and more recently, cybersecurity. My curiosity about the world of cybersecurity has led me to dive deep into topics like cryptography, network security and vulnerability exploitation (obviously, all of this in an ethical way). I'm considering participating in CTFs soon as part of my development, with the possibility of pursuing a professional career in cybersecurity.
Alongside my studies, I've worked on projects that integrate services like Telegram and payment terminals using third party APIs, and I have also used tooles like Docker and Github Pages to deploy services. I'm also a big fan of automation and system management, experimenting with a lot of tools to optimize my workflow.
This blog serves as both my portfolio and a space to share my insights and discoveries in programming and cybersecurity. If you share some of the interests described here or in my blog posts, or maybe you want to share a beer with me, feel free to reach out!

## Personal Interests
### Favorite Music
I like a lot of types of music, but principally I do hear a lot of Hip Hop, Boleros and Indie rock (yeah, weird mix).
Recently, I've been listening to:
 - Supertramp
 - Julio Jaramillo
 - OK Go
 - Cage The Elephant
 
### Favorite Series & Movies
 - Atlanta
 - Sons of Anarchy
 - Mr Robot
 - Lucifer
 - Altered Carbon
 
 And in general, I like everything that has to do with Sci-Fi, Comedy of maybe some criminal stuff :p

### Books I'm reading

Currently, I am revisiting How to Make Friends and Influence Over People - Dale Carnegie, and reading King Warrior Magician Lover - Robert Moore. I was also reading Getting Things Done - Paul Allen.

### Hobbies & Activities
I like to spend time with my friends, going out for bike trips (maybe I have some publications in my blog about it) and playing guitar in my free times. In the future, I'd like to do some bushcraft and car mechanics 




<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ site.title }} - Inicio</title>
    <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
</head>
<body>

    <section id="featured-projects">
        <h2>Featured Projects</h2>
        <div class="projects">
            <div class="project">
                <h3><a href="{{ '/portfolio/disbank' | relative_url }}">Disbank</a></h3>
                <p>.A brief project I made with my friend @DystopianRescuer for a Modeling and Programming Course in school, we made a Java Application connected to a Clip Terminal, minded for shared use of the last one between several local businesses</p>
            </div>
            <div class="project">
                <h3><a href="{{ '/portfolio/eddCanek' | relative_url }}">Data Structures in Java</a></h3>
                <p>Implementations of some popular data structures in Java (with good performance btw)</p>
            </div>
            <div class="project">
                <h3><a href="{{ '/portfolio/peopleCounter' | relative_url }}">People Counter</a></h3>
                <p>Real-time people counter powered by AI models in Python</p>
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
