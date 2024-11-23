<script setup>
import { onMounted, onUnmounted } from "vue";

//example components
import NavbarDefault from "../..//examples/navbars/NavbarDefault.vue";
import DefaultFooter from "../../examples/footers/FooterDefault.vue";
import Header from "../../examples/Header.vue";
import FilledInfoCard from "../../examples/cards/infoCards/FilledInfoCard.vue";

//Vue Material Kit 2 components
import MaterialSocialButton from "@/components/MaterialSocialButton.vue";

// sections
import PresentationCounter from "./Sections/PresentationCounter.vue";
import PresentationPages from "./Sections/PresentationPages.vue";
import PresentationExample from "./Sections/PresentationExample.vue";
import data from "./Sections/Data/designBlocksData";
import BuiltByDevelopers from "./Components/BuiltByDevelopers.vue";
import PresentationTestimonials from "./Sections/PresentationTestimonials.vue";
import PresentationInformation from "./Sections/PresentationInformation.vue";
import EventCarousel from "./Components/EventCarousel.vue"
import ImageButton from "./Components/ImageButton.vue"
import MaterialButton from "@/components/MaterialButton.vue";

//images
import vueMkHeader from "@/assets/img/zagreb.jpg";
import wavesWhite from "@/assets/img/waves-white.svg";
import logoBootstrap from "@/assets/img/logos/bootstrap5.jpg";
import logoTailwind from "@/assets/img/logos/icon-tailwind.jpg";
import logoVue from "@/assets/img/logos/vue.jpg";
import logoAngular from "@/assets/img/logos/angular.jpg";
import logoReact from "@/assets/img/logos/react.jpg";
import logoSketch from "@/assets/img/logos/sketch.jpg";


import kultura from "@/assets/img/kultura.jpg";
import zabava from "@/assets/img/zabava.jpg";
import djeca from "@/assets/img/djeca.jpg";
import kvart from "@/assets/img/kvart.jpg";
import logo from "@/assets/img/logos/logo.png";
import karta from "@/assets/img/karta.jpg";
import MapComponent from "./Components/MapComponent.vue";
import BigButton from "./Components/BigButton.vue";


//hooks
const body = document.getElementsByTagName("body")[0];
onMounted(() => {
  body.classList.add("presentation-page");
  body.classList.add("bg-gray-200");
});
onUnmounted(() => {
  body.classList.remove("presentation-page");
  body.classList.remove("bg-gray-200");
});
</script>

<template>
  <div class="container position-sticky z-index-sticky top-0">
    <div class="row">
      <div class="col-12">
        <NavbarDefault :sticky="true" />
      </div>
    </div>
  </div>
  <Header>
    <div
      class="page-header min-vh-50"
      :style="`background-image: url(${vueMkHeader})`"
      loading="lazy"
    >
      <div class="container">
        <div class="row">
          <div class="col-lg-7 text-center mx-auto position-relative">
            <ImageButton :text="' '" 
          :targetId ="' '"
          :imageUrl="logo"
          style="width:64vh"
          ></ImageButton>

          </div>
        </div>
      </div>
    </div>
  </Header>

  <div class="card card-body blur shadow-blur mx-1 mx-md-4 mt-n6">
    <section class="mb-5">
    <div class="  ">
      <div class="row justify-space-between text-center py-2">
        <div class="d-flex justify-content-around col-12 mx-auto">
          <ImageButton :text="'Zabava'" 
          :targetId ="'zabava-container'"
          :imageUrl="zabava"
          ></ImageButton>
          <ImageButton :text="'Kultura'" 
          :targetId ="'kultura-container'"
          :imageUrl="kultura"
          ></ImageButton>
        </div>
        <div class="d-flex justify-content-around col-12 mx-auto mt-3">
          <ImageButton :text="'Za djecu'" 
          :targetId ="'djeca-container'"
          :imageUrl="djeca"
          ></ImageButton>
          <ImageButton :text="'Na kvartu'" 
          :targetId ="'kvart-container'"
          :imageUrl="kvart"
          ></ImageButton>
        </div>
        <p class="card-text mt-3 text-center" data-v-13a4f36c="">ili
        </p>
        <div class="d-flex justify-content-around col-12 mx-auto">
          <BigButton
          ></BigButton>
        </div>
      </div>
    </div>
  </section>

    
    <h3>Nadolazeći</h3>
    <EventCarousel :type="'nadolazeci'" :defaultImage="vueMkHeader"/>

    <h3 id="zabava-container">Zabava</h3>
    <EventCarousel :type="'zabava'" :defaultImage="zabava"/>
    
    <h3 id="kultura-container">Kultura</h3>
    <EventCarousel :type="'a'" :defaultImage="kultura"/>
    
    <h3 id="djeca-container">Za djecu</h3>
    <EventCarousel :type="'b'" :defaultImage="djeca"/>
    
    <h3 id="kvart-container">Na kvartu</h3>
    <!--EventCarousel :type="'c'" :defaultImage="kvart"/-->
    <!--img :src="karta"/-->
    <MapComponent :center="[40.7128, -74.0060]" :zoom="12" />

    
  </div>
  
  <DefaultFooter />
</template>
