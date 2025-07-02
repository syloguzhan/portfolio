<template>
    <div>
        <section id="about" class="section">
           <h2 data-aos="fade-up" data-aos-delay="200">
              Hello, I'm <span>{{typedName}}</span><span class="cursor">|</span>
           </h2>
           <h2 data-aos="fade-up"> Web Developer & Computer Science Student</h2>
           <p data-aos="fade-up">
              Welcome to my personal portfolio website.
              I am passionate about building web applications and continuously learning new technologies to improve my skills. 
              I enjoy tackling challenging problems, experimenting with innovative ideas, and creating projects that make a positive impact. 
              I strive to combine creativity and technical expertise to deliver high-quality, efficient, and user-friendly software solutions. 
           </p> 
           <p data-aos="fade-up">
             When I'm not coding ,I like reading tech blogs,experimenting with new frameworks.
           </p>
        </section>
        <section id="skilss" class="section">
          <h1 data-aos="fade-up">Skills</h1> 
          <ul class="skill-object">
            <li v-for="(skill,index) in skills"    
                :key="index" 
                :data-aos = "'fade-up'"  
                :data-aos-delay = "index* 75"
                 >  
                <i :class="skill.icon"></i> {{ skill.name }} 
            </li>
          </ul>
        </section> 
        <section id="projects" class="section">
            <h1 data-aos = "fade-up">Projects</h1>
            <div v-for="(project,index) in projects"
                :key="index"
                class="project-card"
                :data-aos="'fade-up'"
                :data-aos-delay="index * 75">
                <h3>{{ project.name }}</h3>
                <p>{{ project.description }}</p>
                <p><strong>Technologies: </strong>{{ project.techStack.join(', ') }}</p> 
                <a v-if="project.github"
                    :href="project.github[0]"
                    target="_blank"
                    rel="noopener"
                    class="github-link">
                    GitHub Repository
                </a>

            </div>

        </section>
        <section id="contacts" class="section">
            <h1 data-aos="fade-up">Contact me</h1>
            <div class="social-ikons" data-aos="fade-up">
                <a href="https://github.com/syloguzhan" target="_blank" rel="noopener" aria-label="GitHub" data-aos="fade-up"><i class="fab fa-github"></i></a>
                <a href="https://www.linkedin.com/in/oguzhan-soylu-a43831273" target="_blank" rel="noopener" aria-label="LinkedIn" data-aos="fade-up"><i class="fab fa-linkedin"></i></a>
                <a href="https://instagram.com/syloguzhan" target="_blank" rel="noopener" aria-label="Instagram"><i class="fab fa-instagram" data-aos="fade-up"></i></a>
                <a href="mailto:oguzhansoylu866@gmail.com" target="_blank" rel="noopener" aria-label="Email"><i class="fas fa-envelope" data-aos="fade-up"></i></a>
            </div>
        </section>
    </div>  
</template>
<script>
import AOS from 'aos';
import 'aos/dist/aos.css'
import '@fortawesome/fontawesome-free/css/all.css';


export default {
    name : 'HomePage',
    mounted() {
        AOS.init();
        this.typeName()
    },
    data() {
        return {
            typedName : '',
            fullName  : 'Oğuzhan SOYLU',            
            skills : [
             { name: 'Vue.js', icon: 'fab fa-vuejs' },
             { name: 'HTML & CSS', icon: 'fab fa-html5' },
             { name: 'Flask' , icon:'fas fa-flask'}, 
             { name: 'Python', icon: 'fab fa-python'},
             { name: 'PostgreSQL', icon: 'fa fa-database'}, 
             { name: "GitHub", icon: "fab fa-github" } 
            ],
            projects : [
                {
                    name : "Library Application",
                    description : "A Library management application developed in Python.Supports adding ,deleting , searching books.",
                    techStack : ["Python,PostgreSQL,Vue.js"],
                    github : ["https://github.com/syloguzhan/libraryapplication"] 
                },
                {
                    name : "Twitter Clone",
                    description : "A Twitter API client built with python.Allows sending and retrieving tweets.",
                    techStack : ['Python,PostgreSQL,Vue.js'],
                    github : ["https://github.com/syloguzhan/twitter"] 
                },
                {
                   name: 'Image Processing',
                   description: 'An Image processing application written in Python. Applies various filters and effects on images.',
                   techStack: ['Python'],
                   github : ["https://github.com/syloguzhan/imageprocessing"] 
                   
                },
                {
                  name: 'MovieMate',
                  description: 'A cinema application developed with Python. Includes movie search and recommendation features.',
                  techStack: ['Python,PostgreSQL,Vue.js'],
                  github : ["https://github.com/syloguzhan/MovieMate"] 
                }
            ]
        }
    },
    methods : {
        typeName() {
            let index = 0
            setInterval(()=> {
                if(index < this.fullName.length){
                    this.typedName += this.fullName[index]
                    index ++; 
                }else{ 
                    this.typedName = ''
                    index = 0             
                }
            },150)
        }
    }    
}
</script>
<style>
.cursor {
    display: inline-block;
    animation:blink 0.7s steps(1) infinite;
}
body {
  background-color: #F0f0f0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
#about {
    margin-top: 100px;    
}
html {
    scroll-behavior: smooth;
    padding: 0;
    margin: 0;
    background: #f0f0f0;
}
.section {
    text-align: center;
    background-color: #f0f0f0;
    padding: 50px 20px;
    min-height: 75vh;
    margin-bottom: 0%;
}
.section h1 {
    margin-top: 0;
    font-size: 40px;
    color: #333;
    margin-bottom: 20px;
}
.section h2 {
    font-size: 24px;
    color: #42b983;
    margin-top: 0;
    margin-bottom: 20px;
}
.section p {
    font-size: 18px;
    max-width: 700px;
    margin: 0 auto 20px auto;
    line-height: 1.6;
    text-align: center;
}
.section ul {
    list-style: none;
    padding: 0;
    max-width: 400px;
    margin: 0 auto;
    gap: 100px;
    display: flex;
    flex-direction: column;
    gap: 15px;
}
.section ul li {
    margin: 10px 0;
    color: #42b983;
    font-size: 24px;
}
.project-card {
  background-color: #42b983;
  border: none;
  padding: 25px 30px;
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.15);
  text-align: center;
  max-width: 800px;
  color: white;
  margin: 30px auto;
  border-radius: 20px;
  transition: transform 1s ease-in,
    box-shadow 1s ease-in-out,
    background-color 1s ease-in-out;
  transform: translateY(0);
}

.project-card:hover {
  transform: translateY(-30px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
  background-color: #146f46;
}
.project-card a {
    display: block;
    color: white;
}
 

.project-card p {
    margin-top: 15px;
    margin-bottom: 15px;
    font-size: 16px;
    color: #e0f7ef;
}
.social-ikons  {
    font-size: 50px;
    margin-top: 100px;
    display: flex;
    flex-direction: row;
    gap: 50px;
    justify-content: center;
}
@media (max-width: 600px;){ 
    .social-ikons {
        font-size: 30px;
        gap: 10px;
        margin-top: 50px;
    }
}
.social-ikons :hover {
    transition: 0.3s ease; 
}
.github-link {
    text-decoration: none;
    color: #e0f7ef;
    font-weight: 600;
    transition: color 0.3 ease;
}
.github-link:hover {
    color:   #42b983;
}
</style>
