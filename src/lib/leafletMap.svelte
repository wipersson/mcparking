<script>
    import { onMount } from 'svelte';
    import { browser } from '$app/env';

    onMount(async () => {
        if(browser) {
            const leaflet = await import('leaflet');

            const map = leaflet.map('map').setView([59.610927, 16.542393], 13);

            leaflet.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
                attribution: '© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
            }).addTo(map);
            let markers = [[59.608761, 16.546065], [59.610927, 16.542393], [59.603247, 16.551152]]
            markers.forEach(element => {
                leaflet.marker(element).addTo(map)
                .bindPopup('En parkeringsplats!')
            });
            
        }
    });
</script>


<main>
    <div id="map" class="h-full"></div>
</main>

<style>
    @import 'https://unpkg.com/leaflet@1.7.1/dist/leaflet.css';
    #map {
        height: 400px;
    }
</style>