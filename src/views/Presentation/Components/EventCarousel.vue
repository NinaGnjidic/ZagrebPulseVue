<template>
    <div class="mb-5">
      <!-- Carousel with Cards -->
      <div v-if="loading">Loading events...</div>
      <div v-else-if="error">{{ error }}</div>
      <div v-else>
        <div :id="type" class="carousel slide" data-bs-ride="carousel">
          <div class="carousel-inner">
            <div
              v-for="(event, index) in events"
              :key="event.id"
              :class="['carousel-item', index === 0 ? 'active' : '']"
            >
              <div class="card" style="width: 21rem;">
                <img 
  v-if="event.fields.slika && event.fields.slika.length > 0 && event.fields.slika[0].url" 
  :src="event.fields.slika[0].url" 
  class="card-img-top" 
  alt="Event image">

<!-- Fallback image when slika is null or empty -->
<img 
  v-else
  :src="defaultImage" 
  class="card-img-top" 
  alt="Default Event Image">
                <div class="card-body" style="padding: 0.5rem;">
                  <h6 class="card-title">{{ event.fields['puni naziv'] }}</h6>
                  <h6 style="font-size: 15px;text-align: left;margin-bottom: 0;">{{ event.organizator[0].fields['ime'] }}</h6>
                  <h6 style="font-size: 15px;text-align: left;">{{ new Intl.DateTimeFormat('hr-HR', { day: '2-digit', month: '2-digit', year: 'numeric', hour: '2-digit', minute: '2-digit' }).format(new Date(event.fields['datum i vrijeme početka'])) }}</h6>
                  <p class="card-text" style="min-height: 50px;max-height: 50px; overflow: hidden; text-overflow: ellipsis;text-align: left;">{{ event.fields['opis'] }}</p>
                  <a :href="event.fields['Poveznica na događaj']" target="_blank" class="btn btn-info">Više</a>
                </div>
              </div>
            </div>
          </div>
  
          <!-- Carousel Controls -->
          <button
            class="carousel-control-prev"
            type="button"
            :data-bs-target="modifiedType"
            data-bs-slide="prev"
          >
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
          </button>
          <button
            class="carousel-control-next"
            type="button"
            :data-bs-target="modifiedType"
            data-bs-slide="next"
          >
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
          </button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    props: {
    type:'',
    defaultImage:''
    
  },
    data() {
      return {
        events: [],
        loading: true,
        error: null
      };
    },
    computed: {
    modifiedType() {
      return '#' + this.type;
    }
  },
    mounted() {
      // Fetch events from both APIs
      this.fetchEvents();
    },
    methods: {
      async fetchEvents() {
        console.log(this.type)
        let url = this.type == "zabava" ? "http://localhost:8081/api/events/zabava" : "http://localhost:8081/api/events";


        try {
          // Fetch events from both endpoints
          const [allEventsResponse] = await Promise.all([
            axios.get(url)
          ]);
  
          // Combine the event data from both responses
          this.events = [ ...allEventsResponse.data];
  
          // Mark loading as complete
          this.loading = false;
        } catch (error) {
          this.error = 'Failed to load events';
          console.error(error);
          this.loading = false;
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .carousel-item {
    text-align: center;
  }
  .card {
    margin: 10px;
  }
  </style>