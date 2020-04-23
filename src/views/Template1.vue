<template>
  <div class="template-page">
    <div class="text-center mb-4">
      <v-btn color="primary" @click="downloadNow">Download</v-btn>
    </div>
    <div class="routine-container">
      <div class="routine" id="routine" ref="routine">
        <div class="date">
          <input type="text" class="date-input" v-model="routineDate" />
        </div>

        <table class="routine-table">
          <thead>
            <tr>
              <th class="column1">শ্রেণী</th>
              <th class="column2">বিষয়</th>
              <th class="column3">সময়</th>
            </tr>
          </thead>

          <tbody>
            <tr v-for="(r, i) in routine" :key="i">
              <td class="column1">
                <input type="text" v-model="r.class" class="table-input" />
              </td>
              <td class="column2">
                <input type="text" v-model="r.subject" class="table-input" />
              </td>
              <td class="column3">
                <input type="text" v-model="r.duration" class="table-input" />
              </td>
            </tr>

            <!-- <tr v-for="(r, i) in routine" :key="i">
              <td>
                <div contenteditable="true" :value="r.class">
                  {{ r.class }}
                </div>
              </td>
              <td>
                <div contenteditable="true" :value="r.subject">
                  {{ r.subject }}
                </div>
              </td>
              <td>
                <div contenteditable="true" :value="r.duration">
                  {{ r.duration }}
                </div>
              </td>
            </tr> -->
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import html2canvas from "html2canvas";

export default {
  data() {
    return {
      routineDate: "২২ এপ্রিলের সময়সুচি",
      routine: [
        {
          class: "৭ম",
          subject: "আরবি ২য় পত্র",
          duration: "বিকাল ৪.০০ - ৪.২০"
        },
        {
          class: "৮ম",
          subject: "আরবি ২য় পত্র",
          duration: "বিকাল ৪.২০ - ৪.৪০"
        },
        {
          class: "৯ম",
          subject: "আরবি ২য় পত্র",
          duration: "বিকাল ৪.৪০ - ৫.০০"
        }
      ]
    };
  },
  mounted() {},
  methods: {
    downloadNow() {
      html2canvas(this.$refs.routine).then(function(canvas) {
        // document.body.appendChild(canvas);
        var a = document.createElement("a");
        // toDataURL defaults to png, so we need to request a jpeg, then convert for file download.
        a.href = canvas
          .toDataURL("image/jpeg")
          .replace("image/jpeg", "image/octet-stream");
        a.download = "template1.jpg";
        a.click();
      });
    }
  }
};
</script>

<style></style>
