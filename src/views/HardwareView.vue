<script setup>
import TheWelcome from "../components/TheWelcome.vue";
</script>

<template>
  <main>
    <div class="p-4 sm:ml-80">
      <div class="p-4">
        <div class="grid grid-cols-3 gap-4 mb-4">
          <h1
            className="text-3xl font-bold underline flex items-center justify-center"
          >
            List Hardware
          </h1>
        </div>
        <table class="table-fixed">
          <thead>
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Category</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(hardware, index) in this.hardwares" :key="index">
              <td>{{ hardware.id }}</td>
              <td>{{ hardware.name }}</td>
              <td>{{ hardware.category.id }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
const authToken =
  "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiIxIiwianRpIjoiYTdjZWI0ODcyNWMyNmYwZTEyNGQ4Yjc5ZDU0OWFmZGQwYzFmOGQzYWUzM2Y0YTJlNjM2Y2U2YmI5NTQxY2ExMzEyNDlmN2MzOTAyOTBmZmMiLCJpYXQiOjE3MDAyNzc2ODcuODUzMDczLCJuYmYiOjE3MDAyNzc2ODcuODUzMDgxLCJleHAiOjIxNzM2NjMyODcuODM0NjA1LCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.rdon5qbmKwXE1bxGVaDLSd3Z_Q9t959OaZXpml2mnY_1NEDGNnTzbHmHY89xraiMMkgVzVwJUgvnQFrgQehg073-0SQBsjiEyWThe4AKHWXitEjulBKi2k0s5IHcFphGc2g6yCoszJv4w3a8UBM-iomccD41DCl6uTXBRGeA1fNOHhSRarbIBKq8Jj8bWgn0aZg9tfp01hJdp5_5BxPrGHW4Tq6q-CjQDMUQLV89k3UfnYX95m3TEvMcdqiIhWYSsAUWqgYI7hmc2YEQEKm7uWKXssBFlXkWHmiv7MeJqhiMRtCvr-Lek0YeS6SaaEP0OqXEeFByIABnaAgbPIyGOQVzzgkW9ucbAw2OjntHEn01BM1dSUe9E90aBCVD7mbe5CCgdvJkKumANi6y-6x-XYlV1NaAQVrXa4yWZr9n4eqo7grv5dvxlYy7YtrCk7EpR_jHLaZXTgQ5oqKGBgyzqrDZd9JwV9D-amE-_J6kwjylhT6RDpecsv24Qp45mir_P0F8Ac8kOzrEkSedIcnHapE62rSOenIuJGY4ih9XaLot85yOwY5_kWQG8OSEiMi9KahPm9R41hdJs8pnUBA0qZxxnAZD-P5yhFvSiH1z7qVPrOj30PHAwWz0Z_dK1mQpYrXKNmMP-NSvvenlS_vjQnCVCt2LZ4Qef6edPg43Ja8";
const headers = {
  Authorization: `Bearer ${authToken}`,
  "Content-Type": "application/json", // Adjust content type if needed
};

export default {
  name: "hardwares",
  data() {
    return {
      hardwares: [],
    };
  },
  mounted() {
    this.getHardware();
  },
  methods: {
    getHardware() {
      axios.get("http://localhost/api/v1/hardware", { headers }).then((res) => {
        this.hardwares = res.data.rows;
        console.log(this.hardwares);
      });
    },
  },
};
</script>
