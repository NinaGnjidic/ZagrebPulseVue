<template>
    <div id="map" ref="mapContainer" style="height: 360px ;width:360px;"></div>
  </template>
  
  <script>
  import L from "leaflet"; // Import Leaflet library
  import "leaflet/dist/leaflet.css";
  import "leaflet.awesome-markers/dist/leaflet.awesome-markers.css";
import "leaflet.awesome-markers";
  
  import "leaflet/dist/leaflet.css";

  // Add this to define a red marker icon
  const redMarker = L.AwesomeMarkers.icon({
  icon: "info-sign", // Bootstrap glyphicon or FontAwesome icon
  markerColor: "red", // Marker color: 'red', 'blue', 'green', etc.
  prefix: "glyphicon", // Icon prefix: 'fa' (FontAwesome) or 'glyphicon'
});
  export default {
  name: "MapComponent",
  data() {
    return {
      map: null,
      userLocation: null, // User's current location
    };
  },
  mounted() {
    // Get the user's current location
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(
        (position) => {
          const { latitude, longitude } = position.coords;
          this.userLocation = [latitude, longitude];
          this.initMap();
          this.addRandomPins();
        },
        (error) => {
          console.error("Geolocation error:", error);
          // Fallback to default location if geolocation fails
          this.userLocation = [51.505, -0.09];
          this.initMap();
        }
      );
    } else {
      console.error("Geolocation not supported");
      // Fallback to default location
      this.userLocation = [51.505, -0.09];
      this.initMap();
    }
  },
  methods: {
    // Initialize the map
    initMap() {
      this.map = L.map(this.$refs.mapContainer).setView(this.userLocation, 13);

      // Add OpenStreetMap tiles
      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        attribution:
          '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
      }).addTo(this.map);

      // Add a marker for the user's current location
      L.marker(this.userLocation, { icon: redMarker })
  .addTo(this.map)
  .bindPopup("Vi ste tu!")
  .openPopup();    },
    // Add random pins within 3 kilometers of the user's location
    addRandomPins() {
      const randomPins = this.generateRandomPins(this.userLocation, 5, 1000); // 5 pins within 3km
      randomPins.forEach((pin) => {
        L.marker(pin).addTo(this.map).bindPopup("Random Pin!");
      });
    },
    // Generate random coordinates within a specified radius (in meters)
    generateRandomPins(center, count, radius) {
      const [lat, lng] = center;
      const pins = [];

      for (let i = 0; i < count; i++) {
        const randomLat = lat + this.getRandomOffset(radius);
        const randomLng = lng + this.getRandomOffset(radius) / Math.cos((lat * Math.PI) / 180);
        pins.push([randomLat, randomLng]);
      }

      return pins;
    },
    // Generate a random offset in degrees for a given radius
    getRandomOffset(radius) {
      const earthRadius = 6371000; // Earth's radius in meters
      const offset = (radius / earthRadius) * (180 / Math.PI); // Convert to degrees
      return (Math.random() - 0.5) * 2 * offset; // Random value between -offset and +offset
    },
  },
};
</script>
  
  <style scoped>
  #map {
    width: 100%;
    height: 100%; /* Take full height of the parent container */
  }
  </style>
  