<template>
  <Nav />
  <section class="banner">
      <div id="about" class="personal-infos">
          <h1>
              Je suis Nathan LEFETEY,
              <br>
              Développeur Fullstack
          </h1>
          <p>
              Développeur de passion, je crée des sites web et application avec un oeil nouveau et professionnel afin de
              répondre au mieux à vos besoins
          </p>
          <a class="personal-docs" href="../public/docs/Cv-Recherche-Alternance-Nathan-LEFETEY.pdf" download>
              <i class="fa-solid fa-download"></i>
              Télécharger mon CV
          </a>
          <div class="personal-links">
              <span>Suivez-moi :</span>
              <a href="https://github.com/jstnate"><i class="fa-brands fa-github"></i></a>
              <a href="https://www.linkedin.com/in/nathanlefetey/"><i class="fa-brands fa-linkedin"></i></a>
              <a href="mailto:lefetey.nathan@gmail.com"><i class="fa-solid fa-envelope"></i></a>
          </div>
      </div>
      <div class="personal-picture">
          <img src="@/assets/images/cover/nathan_lefetey_pic.png" alt="">
      </div>
  </section>
  <div class="date-counter">
      <span class="text main-text">Depuis</span>
      <span id="years" class="number years"></span>
      <span class="text years">ans</span>
      <span class="divider months">|</span>
      <span id="months" class="number months"></span>
      <span class="text months">mois</span>
      <span class="divider days">|</span>
      <span id="days" class="number days"></span>
      <span class="text days">jours</span>
      <span class="divider hours">|</span>
      <span id="hours" class="number hours"></span>
      <span class="text hours">heures</span>
      <span class="divider minutes">|</span>
      <span id="minutes" class="number minutes"></span>
      <span class="text minutes">minutes</span>
  </div>
  <section id="my-services" class="section my-services">
      <h2 class="section__title my-services__title">Mes Services</h2>
      <div class="section__content my-services__content">
          <ServiceCard
              class="right bottom"
              title="ux / ui design"
              description="Réalisation de maquettes de sites web et d'applications pensés et conceptualisés pour vos utilisateur"
              favicon="uxui-bdx.png"
              hoverFavicon="uxui-white.png"
          />
          <ServiceCard
              class="left bottom right"
              title="Web design"
              description="Création des maquettes et des visuels qui feront le charme de votre site web ou de votre application"
              favicon="webdesign-bdx.png"
              hoverFavicon="webdesign-white.png"
          />
          <ServiceCard
              class="left bottom"
              title="Développement front-end"
              description="Conception de la partie visuel et interactive de site web et d’application"
              favicon="front-bdx.png"
              hoverFavicon="front-white.png"
          />
          <ServiceCard
              class="right top"
              title="développement back-end"
              description="Conception de la partie serveur et base de données de site web et d’application"
              favicon="back-bdx.png"
              hoverFavicon="back-white.png"
          />
          <ServiceCard
              class="left top right"
              title="développement mobile"
              description="Réalisation d'application pour smartphone"
              favicon="mobile-bdx.png"
              hoverFavicon="mobile-white.png"
          />
          <ServiceCard
              class="left top"
              title="développement software"
              description="Conception de logiciel et d’application web"
              favicon="software-bdx.png"
              hoverFavicon="software-white.png"
          />

      </div>
  </section>
  <section id="my-projects" class="section my-projects">
    <h2>Mes Projets</h2>
    <ProjectSlider />
  </section>
  <section id="my-skills" class="section my-skills">
      <h2>Mes compétences</h2>
      <div class="section__content my-skills__content">
          <SkillBadge icon="fa-brands fa-html5" title="HTML"/>
          <SkillBadge icon="fa-brands fa-css3-alt" title="CSS"/>
          <SkillBadge icon="fa-brands fa-square-js" title="Javascript"/>
          <SkillBadge icon="fa-brands fa-php" title="PHP"/>
          <SkillBadge icon="fa-solid fa-database" title="MySql"/>
          <SkillBadge icon="fa-brands fa-swift" title="Swift"/>
          <SkillBadge icon="fa-brands fa-python" title="Python"/>
          <SkillBadge icon="fa-brands fa-sass" title="Sass"/>
          <SkillBadge icon="fa-brands fa-vuejs" title="VueJs"/>
          <SkillBadge icon="fa-brands fa-node-js" title="NodeJS"/>
          <SkillBadge icon="fa-brands fa-react" title="React"/>
          <SkillBadge icon="fa-brands fa-laravel" title="Laravel"/>
          <SkillBadge icon="fa-brands fa-symfony" title="Symfony"/>
          <SkillBadge icon="fa-brands fa-wordpress" title="Wordpress"/>
          <SkillBadge icon="fa-brands fa-github" title="Github"/>
          <SkillBadge icon="fa-brands fa-gitlab" title="GitLab"/>
          <SkillBadge icon="fa-brands fa-docker" title="Docker"/>
          <SkillBadge icon="fa-brands fa-yarn" title="Yarn"/>
          <SkillBadge icon="fa-brands fa-npm" title="NPM"/>
          <SkillBadge icon="fa-brands fa-figma" title="Figma"/>
        </div>
  </section>
  <FooterLayout />
</template>
<script>
  import Nav from '@/layouts/NavLayout.vue'
  import moment from 'moment'
  import ServiceCard from "@/components/ServiceCardComponent.vue";
  import SkillBadge from "@/components/SkillBadgeComponent.vue";
  import ProjectSlider from "@/layouts/SliderLayout.vue";
  import FooterLayout from "@/layouts/FooterLayout.vue";
  export default {
      name: "App",
      components: {
          Nav,
          ServiceCard,
          SkillBadge,
          ProjectSlider,
          FooterLayout
      },
      mounted() {
          const yearsDiv = document.getElementById("years");
          const monthsDiv = document.getElementById("months");
          const daysDiv = document.getElementById("days");
          const hoursDiv = document.getElementById("hours");
          const minutesDiv = document.getElementById("minutes");

          function getCurrentTime(givenTimestamp) {
              // créer un objet moment pour le timestamp donné
              let momentGiven = moment.unix(givenTimestamp);

              // créer un objet moment pour l'heure actuelle
              let momentNow = moment();

              // calculer la différence entre les deux moments
              let duration = moment.duration(momentNow.diff(momentGiven));
              let years = duration.years();
              let months = duration.months();
              let days = duration.days();
              let hours = duration.hours();
              let minutes = duration.minutes();

              // mettre à jour l'affichage
              yearsDiv.textContent = yearsDiv !== null ? years : "";
              monthsDiv.textContent = monthsDiv !== null ? months : "";
              daysDiv.textContent = daysDiv !== null ? days : "";
              hoursDiv.textContent = hoursDiv !== null ? hours : "";
              minutesDiv.textContent = minutesDiv !== null ? minutes : "";
          }

          function updateTimeDifference(givenTimestamp) {
              // mettre à jour l'affichage toutes les minutes
              setInterval(() => {
                  getCurrentTime(givenTimestamp);
              }, 10000);
              // actualiser toutes les 60 secondes
          }


          // utiliser la fonction pour mettre à jour l'affichage pour un timestamp donné
          updateTimeDifference(1630497600);
          getCurrentTime(1630497600)
      }
  }
</script>
<style lang="scss" scoped>
  .banner {
      width: 100%;
      background-image: url("@/assets/images/cover/header-background-desktop.png");
      min-height: 90vh;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      margin: 0 auto;
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
      padding: 0 10vw;
      font-family: 'Unbounded', cursive;
      font-size: 16px;

      @media screen and (max-width: 860px){
        background-image: url("@/assets/images/cover/header-background-mobile.png");
        flex-direction: column-reverse;
        align-items: center;
        justify-content: center;
        gap: 50px;
        padding: 1rem 3rem 6rem;
      }

      div {
          height: 100%;
          background: none;

          @media screen and (max-width: 860px){
            width: 80%;
            height: auto;           
          }

          &.personal-infos {
              width: 50%;
              display: flex;
              flex-direction: column;
              justify-content: center;
              align-items: flex-start;

              @media screen and (max-width: 860px){
                width: 80%;
                align-items: center;
                text-align: center;
              }

              h1 {
                  font-size: 28px;
                  font-weight: 700;
                  color: #C5AA86;
                  margin-bottom: 2vh;
                  background: none;
              }

              p {
                  font-size: 16px;
                  font-weight: 400;
                  color: #7D575D;
                  margin-bottom: 5vh;
                  background: none;
              }

              .personal-docs {
                  background-color: #C5AA86;
                  color: #FFFFFF;
                  padding: 1rem 2rem;
                  display: flex;
                  align-items: center;
                  gap: 20px;
                  font-size: 16px;
                  border-radius: 10px;
                  font-weight: bold;
                  transition: all .2s;
                  text-decoration: none;

                  &:hover {
                      background-color: #7D575D;
                  }

                  i {
                      background: none;
                      font-size: 20px;
                  }
              }

              .personal-links {
                  height: auto;
                  margin-top: 70px;
                  display: flex;
                  flex-direction: row;
                  align-items: center;
                  gap: 20px;

                  @media screen and (max-width: 860px) {
                    justify-content: center;
                    margin-top: 50px;
                  }

                  span {
                      font-size: 16px;
                      font-weight: 600;
                      color: #7D575D;
                      background: none;

                      @media screen and (max-width: 860px) {
                        display: none;
                      }
                  }

                  a {
                      background-color: #7D575D;
                      padding: .6em;
                      border-radius: 50%;
                      aspect-ratio: 1/1;
                      display: flex;
                      justify-content: center;
                      align-items: center;
                      transition: all .2s;
                      text-decoration: none;

                      @media screen and (max-width: 860px) {
                        padding: .8em;
                      }

                      &:hover {
                          background-color: #C5AA86;
                      }

                      i {
                          font-size: 24px;
                          color: #FFFFFF;
                          background: none;
                      }
                  }
              }
          }

          &.personal-picture {
              width: 40%;
              display: flex;
              justify-content: center;
              align-items: flex-end;

              @media screen and (max-width: 860px) {
                width: 80%;
              }

              img {
                  width: 100%;
                  background: none;

                  @media screen and (max-width: 860px){
                    width: 70%;
                    border-radius: 50%;
                  }
              }
          }
      }

  }

  .date-counter {
      width: 100%;
      background-color: #C5AA86;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 15vh;
      font-family: 'Josefin sans', sans-serif;

      @media screen and (max-width: 860px) {

        .minutes {
            display: none;
        }
    }

      span {
          color: #FFFFFF;
          background: none;
          font-size: 32px;
          font-weight: 300;

          &.text {
              margin: 0 15px 0 5px;

              &.main-text {
                  margin-right: 100px;

                  @media screen and (max-width: 860px) {
                      margin-right: 50px;
                  }
              }
          }

          &.divider {
              margin: 0 40px 0 20px;
              font-size: 44px;
              font-weight: 900;
          }

          &.number {
              font-size: 44px;
              font-weight: 900;
          }
      }
  }

  .section {
      width: 100%;
      min-height: 90vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 150px 0 100px;
      gap: 100px;

      &:hover {
          h2 {
              &::before, &::after {
                  transform: scaleX(1) scaleY(1);
              }
          }
      }

      h2 {
          font-size: 40px;
          text-align: center;
          width: 50%;
          padding: 10px 0;
          font-weight: 900;
          font-family: 'Josefin sans', sans-serif;
          color: #7D575D;
          position: relative;

          @media screen and (max-width: 860px) {
              width: 80%;
          }

          &::before, &::after {
              content: "";
              position: absolute;
              display: flex;
              width: 100%;
              height: 110%;
              transform: scaleX(0) scaleY(0);
              transition: transform .5s;
          }

          &::before {
              top: -10px;
              left: 0;
              transform-origin: top right;
              border-top: 3px solid #7D575D;
              border-right: 3px solid #7D575D;
          }

          &::after {
              bottom: 0px;
              right: 1;
              transform-origin: bottom left;
              border-bottom: 3px solid #7D575D;
              border-left: 3px solid #7D575D;
          }
      }
  }

  @keyframes titleFrame {
      0% {
          transform: scaleX(0) scaleY(0);
      }
      50% {
          transform: scaleX(1) scaleY(0);
      }
      100% {
          transform: scaleX(1) scaleY(1);
      }
  }

  .my-services {
    width: 80%;
    margin: auto;
    padding: 150px 0 0;
    &__content {
          width: 80%;
          display: grid;
          grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));

          .top {
              border-top: 1px solid #7D575D;
          }
          .right {
              border-right: 1px solid #7D575D;
          }
          .bottom {
              border-bottom: 1px solid #7D575D;
          }
          .left {
              border-left: 1px solid #7D575D;
          }

          @media screen and (max-width: 860px) {
             display: flex;
             flex-direction: column;
             align-items: center;

            & > #service-card:nth-last-child(n+2) {
                border-bottom: 2px solid #7D575D;
            }
            
            .top, .right, .bottom, .left {
                border: none;
            }
          }
      }
  }

  .my-skills {
      background-color: #7D575D;

      h2 {
          background-color: #7D575D;
          color: #F9F9F9;

          &::before, &::after {
              border-color: #F9F9F9;
          }
      }

      &__content {
          background: none;
          display: grid;
          width: 80%;
          margin-left: 10vw;
          grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
          place-items: center;
          gap: 20px;

          @media screen and (max-width: 860px) {
              place-items: start;
          }
      }
  }
</style>
