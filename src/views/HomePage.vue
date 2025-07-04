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
           <div ref="lottieContainer1" class="animation1"></div>
        </section>
        <section id="skills" class="section">
          <h1 data-aos="fade-up">Skills</h1> 
          <div class="skill-container">
                <div>
                    <ul class="skill-object">             
                        <li v-for="(skill,index) in skills"    
                            :key="index" 
                            :data-aos = "'fade-up'"  
                            :data-aos-delay = "index* 75"
                            >  
                            <i :class="skill.icon"></i> {{ skill.name }} 
                        </li>
                    </ul>
                </div> 
                <div ref="lottieContainer2" class="animation2"></div>
          </div>
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
                <a href="https://github.com/syloguzhan" target="_blank" rel="noopener" aria-label="GitHub" ><i class="fab fa-github" data-aos="fade-up"></i></a>
                <a href="https://www.linkedin.com/in/oguzhan-soylu-a43831273" target="_blank" rel="noopener" aria-label="LinkedIn" ><i class="fab fa-linkedin" data-aos="fade-up"></i></a>
                <a href="https://instagram.com/syloguzhan" target="_blank" rel="noopener" aria-label="Instagram"><i class="fab fa-instagram" data-aos="fade-up"></i></a>
                <a href="mailto:oguzhansoylu866@gmail.com" target="_blank" rel="noopener" aria-label="Email"><i class="fas fa-envelope" data-aos="fade-up"></i></a>
            </div> 
        <button
                v-show="showBackToTop"
                @click="scrollToTop"
                class="back-to-top">
                Back to top
        </button>  
        </section>

    </div>  
</template>
<script>
import AOS from 'aos';
import 'aos/dist/aos.css'
import '@fortawesome/fontawesome-free/css/all.css';
import Lottie from 'lottie-web';
import animantionData1 from '@/assets/Animation1.json'
import animationData2 from '@/assets/Animation2.json'
import 'bootstrap'


export default {
    name : 'HomePage',
    mounted() {
        AOS.init();
        this.typeName()
        Lottie.loadAnimation({
            container: this.$refs.lottieContainer1,
            renderer : 'svg',
            loop : true,
            autoplay : true,
            animationData : animantionData1 
        })
        Lottie.loadAnimation({
            container: this.$refs.lottieContainer2,
            renderer : 'svg',
            loop : true,
            autoplay : true,
            animationData : animationData2           
        })
        window.addEventListener('scroll',this.handleScroll)

    },
    beforeDestroy() {
        window.removeEventListener('scroll', this.handleScroll);

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
            ],
            showBackToTop :false 
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
        },
        scrollToTop() {
            window.scrollTo({
                top:0, 
                behavior:'smooth'             
            });
        },
        handleScroll() {
            this.showBackToTop = window.scrollY > 200; 
        },

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
    max-width: 500px;
    margin: 0 auto;
    gap: 100px;
    display: flex;
    flex-direction: column;
    gap: 15px;
    margin-left: 35px;
}
.animation2 {
    margin-right: 0px;
    width: 500px;
}
.skill-container {
    display: flex;
    flex-direction: row;
    gap: 10px;
    align-items: center;
    justify-content:space-around;
    margin-top: 40px;
    
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
  transition: transform 1s ease,
    box-shadow 1s ease,
    background-color 2s ease;
  transform: translateY(0);
}

.project-card:hover {
  transform: translateY(-30px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.30);
  background-color: #146f46;
}
.project-card a {
    display: block;
    color: #f0f0f0;
}
 

.project-card p {
    margin-top: 15px;
    margin-bottom: 15px;
    font-size: 16px;
    color: #e0f7ef;
}
.social-ikons {
    font-size: 50px;
    margin-top: 100px;
    display: flex;
    flex-direction: row;
    gap: 50px;
    justify-content: center;
    cursor: pointer;
}
.social-ikons a {
    color:  #42b983; 
    transition:color 0.6s;
}
.social-ikons a:hover {
    color: black;

}
@media (max-width: 600px){ 
    .social-ikons a {
        font-size: 30px;
        gap: 10px;
        margin-top: 50px;
    }
}
.github-link  {
    text-decoration: none;
    color: #e0f7ef; 
    font-weight: 600;
    transition: color 0.5 ease;
}
.github-link:hover {
    color:   #42b983;
}
.animation1 {
    align-content: center;
    margin: auto;
    width: 33%;
}
.back-to-top {
    background-color: #42b983;
    border: none;
    padding: 15px 15px;
    border-radius: 20px;
    margin-top: 100px;
    cursor: pointer;
    color: white;
    transition: background-color 0.6s ease ;
} 
.back-to-top:hover {
    background-color: #333; 
}
</style>
