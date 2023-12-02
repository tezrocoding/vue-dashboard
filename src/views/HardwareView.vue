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
  "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI5IiwianRpIjoiMDRkNzk1YmQyYzZmZGZiN2UyN2JjN2JiMmUwNTc0NWVhMTEwMmI0OGNiMzMwZDEyNzlkZWRlNzI4ZjhlNzExYzEwYjc1ODJjYmNlZTlhODgiLCJpYXQiOjE3MDE0MTM5OTMuNzg0NTQ0OTQ0NzYzMTgzNTkzNzUsIm5iZiI6MTcwMTQxMzk5My43ODQ1NDk5NTE1NTMzNDQ3MjY1NjI1LCJleHAiOjIxNzQ3OTk1OTMuNzU4OTA2ODQxMjc4MDc2MTcxODc1LCJzdWIiOiIxIiwic2NvcGVzIjpbXX0.lwKR69Yu0xnSIPlfbX6EvOB5h0DzVqKC1T0tKWshXflw_ezNg6tDikVINv2yn_CuT40fQkfeGIZO8S3Hc0IJ7gEjjo32voit81h_ElF1mN7uG6CzSvcHq-PVXFppPYzPV4cRCrqkPBSYpwl3Q8dPkw3_i4IyHJ11yI8hLUVDF-ITx504XjJHenSCXj7H_kenUqa720pfFlnqXtxQnHZ7RB__ei0yVqwBmec8YpR8BfzZN6ACXxjYZDfJjkhGWNhmAFs9sEXjYw6yTlXYUqS_gxPFo6xWD1PXMrlblMcMbco1VNH7owjzy8xrWO8HonFrKHm2kkO2E1sZwUqBfaWHITGQzaXrjhqCYYMiqT_CuJeCjn0uWCNI1FAIxXdj9GfbLjaP62qLi0DBIzKImWSYSZZWo0gTzurrnjJcbG8zQVfWHfq4vBP4WloA_HQ_qOedLpzvho5z0znD0JcU5hXMwyuTK8J5Jzgd3LXVRtG4skxnqJqHZLfxXBxI38Ro5Px3HDAvS7DDVFXlQLbHmLjfWlA93AmU51bvskEQdkRD1xU45-PG_6bScrk3qCc4OQ1xAdGYM57bP3uiCS3ITd1LGmWPSWK0IbdAXJO2W5iNUnk9u4oKZIoNEaV1e4uzpg-u2vBejpThkqxzkZ_rbsc88Um3esBMRW7mPrzVaiXQpP8";
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
      axios
        .get("https://mania.bps.go.id/public/api/v1/hardware", { headers })
        .then((res) => {
          this.hardwares = res.data.rows;
          console.log(this.hardwares);
        });
    },
  },
};
</script>
