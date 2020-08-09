<template>
<div class="home">
    <div class="header">
        <div class="header-content">
            <h1>Ivar {{ '&' }} Ineta's HAIR'N BEAURY</h1>

            <button class="button is-primary is-medium modal-btn"
                @click="isComponentModalActive = true">
                Book online now
            </button>
        </div>
    </div>


    <div class="content services">
        <div class="container">
            <div class="row">
                <div class="column">
                    <h2>Our Services</h2>
                    <section>
                        <div class="service-image">
                            <img :src="require('../assets/haircut.jpeg')">
                        </div>
                        <div class="info">
                            <h4>Regular Haircut</h4>
                            <p>Price: 15£</p>
                            <p>Duration: 20min</p>
                        </div>
                    </section>

                    <section>
                        <div class="service-image">
                            <img :src="require('../assets/fade.jpeg')">
                        </div>
                        <div class="info">
                            <h4>Fade</h4>
                            <p>Price: 30£</p>
                            <p>Duration: 40min</p>
                        </div>
                    </section>
                </div>
                <div class="column">
                    <h2>Opening Times</h2>
                    <table class="openingHours">
                        <tbody><tr itemprop="openingHours" datetime="Mo 09:30-17:30">
                        <td class="openingHours--day">Monday</td>
                        <td class="openingHours--open">09:30 - 17:30</td>
                        </tr>
                        <tr itemprop="openingHours" datetime="We 09:30-19:00">
                        <td class="openingHours--day">Wednesday</td>
                        <td class="openingHours--open">09:30 - 19:00</td>
                        </tr>
                        <tr itemprop="openingHours" datetime="Th 09:30-17:30">
                        <td class="openingHours--day">Thursday</td>
                        <td class="openingHours--open">09:30 - 17:30</td>
                        </tr>
                        <tr itemprop="openingHours" datetime="Fr 09:30-17:30">
                        <td class="openingHours--day">Friday</td>
                        <td class="openingHours--open">09:30 - 17:30</td>
                        </tr>
                        <tr itemprop="openingHours" datetime="Sa 08:00-17:00">
                        <td class="openingHours--day">Saturday</td>
                        <td class="openingHours--open">08:00 - 17:00</td>
                        </tr>
                        <tr class="openingHours--current" itemprop="openingHours" datetime="Su 11:00-17:00">
                        <td class="openingHours--day">Sunday</td>
                        <td class="openingHours--open">11:00 - 17:00</td>
                        </tr>
                    </tbody></table>
                </div>
                </div>
        </div>
    </div>

    <div class="content">
        <div class="container">
            <h2 class="section-title">Our Location</h2>
        </div>
    </div>
    <div class="content location">
         <l-map
      v-if="showMap"
      :zoom="zoom"
      :center="center"
      :options="mapOptions"
      style="height: 300px"
      @update:center="centerUpdate"
      @update:zoom="zoomUpdate"
    >
      <l-tile-layer
        :url="url"
        :attribution="attribution"
      />
      <l-marker :lat-lng="withPopup">
        <l-popup>
          <div @click="innerClick">
            I am a popup
            <p v-show="showParagraph">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
              sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
              Donec finibus semper metus id malesuada.
            </p>
          </div>
        </l-popup>
      </l-marker>
      <l-marker :lat-lng="withTooltip">
        <l-tooltip :options="{ permanent: true, interactive: true }">
          <div @click="innerClick">
            Ivor {{'&'}} Ineta
            <p v-show="showParagraph">
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque
              sed pretium nisl, ut sagittis sapien. Sed vel sollicitudin nisi.
              Donec finibus semper metus id malesuada.
            </p>
          </div>
        </l-tooltip>
      </l-marker>
    </l-map>
    </div>

    <div class="footer">
        <div class="container">
            <p>Contact Number: 0131 111 2345</p>
        </div>
    </div>

    <b-modal
        :active.sync="isComponentModalActive"
        has-modal-card
        trap-focus
        :destroy-on-hide="false"
        aria-role="dialog"
        aria-modal
    >
        <form action="" @submit.prevent="submit" v-if="notSubmitted">
            <div class="modal-card">
                <header class="modal-card-head">
                    <p class="modal-card-title">
                        Book your next haircut appointment
                        <br>
                        <small>We just need few details from you. Once we've recieved your request, we will get back with <strong>confirmation</strong>.</small>
                    </p>
                </header>
                <section class="modal-card-body">
                    <div class="row">
                        <div class="column">
                            <p>Your Details</p>

                            <b-field label="Your Full Name">
                                <b-input
                                    type="text"
                                    :value="fullName"
                                    placeholder="John Smith"
                                    required>
                                </b-input>
                            </b-field>

                            <b-field label="Your Email">
                                <b-input
                                    type="email"
                                    :value="email"
                                    placeholder="Your email"
                                    required>
                                </b-input>
                            </b-field>

                            <b-field label="Your Contact Number">
                                <b-input
                                    type="text"
                                    :value="phone"
                                    placeholder="07........."
                                    required>
                                </b-input>
                            </b-field>
                        </div>

                        <div class="column">
                            <p>Pick a service Details</p>

                            <b-field label="Select Appointment Date and Time">
                                <b-datetimepicker
                                    placeholder="Type or select a date..."
                                    editable>
                                </b-datetimepicker>
                            </b-field>

                            <b-field label="Select service">
                                <b-select
                                    placeholder="Service"
                                    expanded
                                    :value="service"
                                >
                                    <option value="1">Normal Haircut</option>
                                    <option value="2">Fade</option>
                                </b-select>
                            </b-field>
                        </div>
                    </div>

                </section>
                <footer class="modal-card-foot text-left">
                    <button class="button" type="button" @click="isComponentModalActive = false">Cancel</button>
                    <button class="button is-primary">Request Booking</button>
                </footer>
            </div>
        </form>
        <div v-else>
            <div class="modal-card">
                <header class="modal-card-head">
                    <p class="modal-card-title">
                        Thank you for booking!
                    </p>
                </header>
                <section class="modal-card-body">
                    <p>We have sent you an email to {{email}} with the details of the booking. Our members of staff will review your booking and get back ASAP with confirmation.</p>
                </section>
                <footer class="modal-card-foot text-left">
                    <button class="button" type="button" @click="isComponentModalActive = false; notSubmitted = true;">Close</button>
                </footer>
            </div>
        </div>
    </b-modal>
</div>
</template>

<script>
import { latLng } from "leaflet";
import { Icon } from 'leaflet';

delete Icon.Default.prototype._getIconUrl;
Icon.Default.mergeOptions({
  iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
  iconUrl: require('leaflet/dist/images/marker-icon.png'),
  shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
});
import { LMap, LTileLayer, LMarker, LPopup, LTooltip } from "vue2-leaflet";
export default {
    name: 'Home',
    data() {
        return {
            isComponentModalActive: false,
            notSubmitted: true,
            email: null,
            phone: null,
            service: null,
            fullName: null,
            zoom: 18,
            center: latLng(55.96438948898518, -3.176760077476501),
            url: 'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
            attribution:
                '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
            withPopup: latLng(55.96438948898518, -3.176760077476501),
            withTooltip: latLng(55.96438948898518, -3.176760077476501),
            currentZoom: 11.5,
            currentCenter: latLng(55.96438948898518, -3.176760077476501),
            showParagraph: false,
            mapOptions: {
                zoomSnap: 0
            },
            showMap: true
        }
    },

    methods: {
        submit() {
            this.notSubmitted = false;
        },
        zoomUpdate(zoom) {
        this.currentZoom = zoom;
        },
        centerUpdate(center) {
        this.currentCenter = center;
        },
        showLongText() {
        this.showParagraph = !this.showParagraph;
        },
        innerClick() {
            return false;
        }
    },
components: {
    LMap,
    LTileLayer,
    LMarker,
    LPopup,
    LTooltip
  },
}
</script>

<style lang="scss" scoped>
    .header {
        height: 60vh;
        position: relative;
        background-size: cover;
        background-repeat: no-repeat;


        &:after {
            content: '';
            position: absolute;
            background: rgba(0, 0, 0, 0.82);
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
        }
    }

    .services {
        background: rgba(0, 0, 0, 0.05);
        padding: 30px;

        section {
            display: flex;
            margin: 20px 0;

            .info {
                min-width: 300px;
                padding: 20px;
                display: flex;
                flex-direction: column;
                justify-content: center;
            }
        }
    }

    .location {
        position: relative;
    }

    .section-title {
        padding-top: 0.5em;
    }

    .content {
        margin: 0 !important;
    }

    .row {
        display: flex;
    }

    .modal-btn {
        margin-top: 20px;
    }

    small {
        font-size: 50%;
    }

    .vue-map-container {
        width: 100% !important;
    }

    .modal.is-active {
        z-index: 999;
    }

    .header-content {
        position: absolute; 
        top: 50%;
        transform: translateY(-50%);
        left: 10px;
        right: 10px;
        text-align: center;
        z-index: 1;
    }

    h1 {
        font-size: 30px;
        color: #fff;
    }
</style>