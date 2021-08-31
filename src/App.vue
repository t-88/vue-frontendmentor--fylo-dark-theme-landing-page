<template>
  <header id="header">
    <NavBar />
    <Intro />
  </header>
  <body>
    <section id="features">
      <Card :img_path="svg_access_anywhere" title="Access your files, anywhere" description="The ability to use a smartphone, tablet, or computer to access your account means your files follow you everywhere."/>
      <Card :img_path="svg_security" title="Security you can trust" description="2-factor authentication and user-controlled encryption are just a couple of the security features we allow to help secure your files."/>
      <Card :img_path="svg_collaboration" title="Real-time collaboration" description="Securely share files and folders with friends, family and colleagues for live collaboration. No email attachments required."/>
      <Card :img_path="svg_any_file" title="Store any type of file" description="Whether you're sharing holidays photos or work documents, Fylo has you covered allowing for all file types to be securely stored and shared."/>
    </section>
    <section id="how-it-works">
      <HalfImgHalfText :img_path="png_stay_prodactive" title=" Stay productive, wherever you are"  url="See how Fylo works" :description="['Never let location be an issue when accessing your files. Fylo has you covered for all of your file storage needs.','Securely share files and folders with friends, family and colleagues for live collaboration. No email attachments required.'] "/>
    </section>
    <section id="comments">
      <CommentCard v-for="name , index in user_names" :key=index :text="comment_text" :user="{name,jop,img: require(`./assets/profile-${index+1}.jpg`)}"/>
    </section>
      <ContactForm />
  </body>
  <Footer />

</template>

<script>
import NavBar from "./components/NavBar"
import Intro from "./components/Intro"
import Card from "./components/Card"
import HalfImgHalfText from "./components/HalfImgHalfText"
import CommentCard from "./components/CommentCard"
import ContactForm from "./components/ContactForm"
import Footer from "./components/Footer"

export default {
  name: 'App',
  components: {
    NavBar,
    Intro,
    Card,
    HalfImgHalfText,
    CommentCard,
    ContactForm,
    Footer,
  },
  data() {
    return {
      //featchers
      svg_access_anywhere: require("./assets/icon-access-anywhere.svg"),
      svg_security: require("./assets/icon-security.svg"),
      svg_collaboration: require("./assets/icon-collaboration.svg"),
      svg_any_file: require("./assets/icon-any-file.svg"),
    
      //how it works
      png_stay_prodactive: require("./assets/illustration-stay-productive.png"),
    
      //commnets
      comment_text: "Fylo has improved our team productivity by an order of magnitude. Since making the switch our team has become a well-oiled collaboration machine.",
      jop: "Founder & CEO, Huddle",
      user_names: ["Satish Patel", "Bruce McKenzie", "Iva Boyd"]
      }
  }
}
</script>

<style lang="scss">
@import "./shared";

@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap');

html {
  min-width: 320px;
}
html,body,#app {
  width: 100%;
  height: fit-content;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Raleway', sans-serif;
}
#app {
  background: hsl(218, 28%, 13%);

  header {
    background: hsl(217, 28%, 15%);
    background-repeat: no-repeat;

    @include media("<=pc",">tablet") {
      background-image: url("./assets/bg-curvy-desktop.svg");
      background-position: applyMath(0,-80,$pc,$tablet) applyMath(500,570,$pc,$tablet);
      background-size: applyMath(1815,800,$pc,$tablet);
    }
    @include media("<=tablet",">min-width") {
      background-image: url("./assets/bg-curvy-mobile.svg");
      background-position: applyMath(-65,-80,$tablet,320) applyMath(525,380,$tablet,320);
      background-size: applyMath(800,500,$tablet,320);
    }
    @include media("<=min-width") {
      background-image: url("./assets/bg-curvy-mobile.svg");
      background-position: -80px 380px;
      background-size: 500px;
    }
  }
  body {
    padding-bottom: 40px;
    #features {
      display: grid;
      grid-template-columns: 1fr 1fr;
      padding: 0px applyMath(250,50,$pc,$tablet);
      padding-top: applyMath(150,60,$pc,320);
      row-gap: applyMath(100,40,$pc,$tablet);

      @include media("<=tablet") {
        grid-template-columns: auto;
        row-gap: 70px;
      }
    }
    #how-it-works {
      padding-top: applyMath(150,50,$pc,$tablet);
    }
    #comments {
      display: flex;
      justify-content: space-around;

      background-image: url("./assets/bg-quotes.png");
      background-repeat: no-repeat;
      background-position: 0 applyMath(120,37,$pc,$tablet);
      background-size: applyMath(55,50,$pc,$tablet);
    
      margin: auto;
      width: applyMath(1655,530,$pc,$tablet);
      gap: applyMath(50,15,$pc,320);

      padding-top: applyMath(150,50,$pc,320);
      @include media("<=tablet",">min-width"){
        flex-direction: column;
        width: applyMath(480,270,$tablet,320);
        background-position: 0 applyMath(40,34,$tablet,320);
        background-size: applyMath(44,25,$tablet,320);

      }
      @include media("<=min-width") {
        flex-direction: column;
        width: 270px;
        padding-top: 50px;

        background-position: 0 34px;
        background-size: 25px;
      }
    }
  }
  
}
</style>
