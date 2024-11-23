<script setup>
import logoDark from "@/assets/img/logo-ct-dark.png";
defineProps({
  brand: {
    type: Object,
    name: String,
    logo: String,
    route: "",
    default: () => ({
      name: "Material Kit 2",
      logo: logoDark,
      route: "/"
    })
  },
  socials: {
    type: Array,
    icon: String,
    link: String,
    default: () => [
      {
        icon: '<i class="fab fa-facebook text-lg opacity-8"></i>',
        link: "https://www.facebook.com/CreativeTim/"
      },
      {
        icon: '<i class="fab fa-twitter text-lg opacity-8"></i>',
        link: "https://twitter.com/creativetim"
      },
      {
        icon: '<i class="fab fa-dribbble text-lg opacity-8"></i>',
        link: "https://dribbble.com/creativetim"
      },
      {
        icon: '<i class="fab fa-github text-lg opacity-8"></i>',
        link: "https://github.com/creativetimofficial"
      },
      {
        icon: '<i class="fab fa-youtube text-lg opacity-8"></i>',
        link: "https://www.youtube.com/channel/UCVyTG4sCw-rOvB9oHkzZD1w"
      }
    ]
  },
  menus: {
    type: Array,
    name: String,
    items: {
      type: Array,
      name: String,
      href: String
    },
    default: () => [
      {
        name: "company",
        items: [
          {
            name: "about us",
            href: "https://www.creative-tim.com/presentation"
          },
          {
            name: "freebies",
            href: "https://www.creative-tim.com/templates/free"
          },
          {
            name: "premium tools",
            href: "https://www.creative-tim.com/templates/premium"
          },
          { name: "blog", href: "https://www.creative-tim.com/blog" }
        ]
      },
      {
        name: "resources",
        items: [
          { name: "illustrations", href: "https://iradesign.io/" },
          {
            name: "bits & snippets",
            href: "https://www.creative-tim.com/bits"
          },
          {
            name: "affiliate program",
            href: "https://www.creative-tim.com/affiliates/new"
          }
        ]
      },
      {
        name: "help & support",
        items: [
          {
            name: "contact us",
            href: "https://www.creative-tim.com/contact-us"
          },
          {
            name: "knowledge center",
            href: "https://www.creative-tim.com/knowledge-center"
          },
          {
            name: "custom development",
            href: "https://services.creative-tim.com/"
          },
          {
            name: "sponsorships",
            href: "https://www.creative-tim.com/sponsorships"
          }
        ]
      },
      {
        name: "legal",
        items: [
          {
            name: "terms & conditions",
            href: "https://www.creative-tim.com/terms"
          },
          {
            name: "privacy policy",
            href: "https://www.creative-tim.com/privacy"
          },
          {
            name: "licenses (EULA)",
            href: "https://www.creative-tim.com/license"
          }
        ]
      }
    ]
  }
});
</script>
<template>
  <div class="offcanvas offcanvas-start" tabindex="-1" id="offcanvasExample" aria-labelledby="offcanvasExampleLabel">
  <div class="offcanvas-header">
    <h4 class="offcanvas-title" id="offcanvasExampleLabel">Ispuni mi dan</h4>

    <button type="button" class="btn text-reset" style="color:black ;" data-bs-dismiss="offcanvas" aria-label="Close">X</button>
  </div>
  <div class="offcanvas-body">
    <h5 class="offcanvas-title" id="offcanvasExampleLabel">Vrijeme</h5>
    <input type="datetime-local" class="form-control" id="datetimeInput" name="datetimeInput">

    <h5 class="offcanvas-title" id="offcanvasExampleLabel">Kategorija</h5>

    <div class="d-flex flex-wrap gap-2">
          <!-- Checkbox 1: Koncert -->
          <input type="checkbox" class="btn-check" name="eventType" id="koncert" autocomplete="off">
          <label class="btn btn-outline-primary btn-lg" for="koncert">Koncert</label>

          <!-- Checkbox 2: Festival -->
          <input type="checkbox" class="btn-check" name="eventType" id="festival" autocomplete="off">
          <label class="btn btn-outline-primary btn-lg" for="festival">Festival</label>

          <!-- Checkbox 3: Izložba -->
          <input type="checkbox" class="btn-check" name="eventType" id="izlozba" autocomplete="off">
          <label class="btn btn-outline-primary btn-lg" for="izlozba">Izložba</label>

          <!-- Checkbox 4: Predstava -->
          <input type="checkbox" class="btn-check" name="eventType" id="predstava" autocomplete="off">
          <label class="btn btn-outline-primary btn-lg" for="predstava">Predstava</label>

          <!-- Checkbox 5: Performans -->
          <input type="checkbox" class="btn-check" name="eventType" id="performans" autocomplete="off">
          <label class="btn btn-outline-primary btn-lg" for="performans">Performans</label>
        </div>
        <button type="button" class="btn btn-info"> Pretraži</button>

  </div>
</div>
  <footer class="footer pt-5 mt-5">
    <div class="container">
      <!--div class="row">
        <div class="col-md-3 mb-4 ms-auto">
          <div>
            <a :href="brand.route">
              <img :src="brand.logo" class="mb-3 footer-logo" alt="main_logo" />
            </a>
            <h6 class="font-weight-bolder mb-4">{{ brand.name }}</h6>
          </div>
          <div>
            <ul class="d-flex flex-row ms-n3 nav">
              <li
                class="nav-item"
                v-for="{ icon, link } of socials"
                :key="link"
              >
                <a
                  class="nav-link pe-1"
                  :href="link"
                  target="_blank"
                  v-html="icon"
                >
                </a>
              </li>
            </ul>
          </div>
        </div>
        <div
          class="col-md-2 col-sm-6 col-6 mb-4"
          v-for="{ name, items } of menus"
          :key="name"
        >
          <h6 class="text-sm">{{ name }}</h6>
          <ul class="flex-column ms-n3 nav">
            <li class="nav-item" v-for="item of items" :key="item.name">
              <a class="nav-link" :href="item.href" target="_blank">
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>

        <div class="col-12">
          <div class="text-center">
            <p class="text-dark my-4 text-sm font-weight-normal">
              All rights reserved. Copyright ©
              {{ new Date().getFullYear() }}
              Material Kit by
              <a href="https://www.creative-tim.com" target="_blank"
                >Creative Tim</a
              >.
            </p>
          </div>
        </div>
      </div-->
    </div>
  </footer>
</template>
