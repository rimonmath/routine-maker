<template>
  <div class="template-page">
    <div class="text-center mb-4">
      <v-btn color="primary" @click="downloadNow">Download</v-btn>
    </div>
    <div class="routine-container">
      <div class="routine routine--template2" id="routine" ref="routine">
        <div class="date">
          <input type="text" class="date-input" v-model="routineDate" />
        </div>

        <table class="routine-table">
          <thead>
            <tr>
              <th class="column1">শ্রেণী</th>
              <th class="column2">১ম পিরিয়ড</th>
              <th class="column3">২য় পিরিয়ড</th>
            </tr>
          </thead>

          <tbody>
            <tr>
              <td colspan="3">
                <input type="text" v-model="coronaBreak" class="corona-input" />
              </td>
            </tr>
            <tr v-for="(r, i) in routine" :key="i">
              <td class="column1">
                <input type="text" v-model="r.class" class="table-input" />
              </td>
              <td class="column2">
                <input type="text" v-model="r.subject1" class="table-input" />
                <input
                  type="text"
                  v-model="r.time1"
                  class="table-input"
                  v-if="r.time1"
                />
              </td>
              <td class="column3">
                <input type="text" v-model="r.subject2" class="table-input" />
                <input
                  type="text"
                  v-model="r.time2"
                  class="table-input"
                  v-if="r.time2"
                />
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
      routineDate: "২৩ এপ্রিলের সময়সুচি",
      coronaBreak: "জাতীয় সঙ্গীত ও করোনা সচেতনতা (সকাল ১১ঃ০০-১১ঃ০৫)",
      routine: [
        {
          class: "৬ষ্ঠ",
          subject1: "বাংলা",
          time1: "(সকাল ১১.০৫)",
          subject2: "ইংরেজি",
          time2: "(সকাল ১১.৪৫)"
        },
        {
          class: "৭ম",
          subject1: "গণিত (সকাল ১১.৪৫)",
          time1: "",
          subject2: "বিজ্ঞান (দুপুর ১২.২৫)",
          time2: ""
        },
        {
          class: "৮ম",
          subject1: "বাংলা",
          time1: "(দুপুর ১২.২৫)",
          subject2: "গণিত",
          time2: "(দুপুর ১.০৫)"
        },
        {
          class: "৯ম",
          subject1: "গণিত",
          time1: "(দুপুর ১.০৫)",
          subject2: "ইংরেজি",
          time2: "(দুপুর ১.৪৫)"
        },
        {
          class: "১০ম",
          subject1: "ইংরেজি",
          time1: "(দুপুর ১.৪৫)",
          subject2: "রসায়ন",
          time2: "(দুপুর ২.২৫)"
        }
      ]
    };
  },
  mounted() {},
  methods: {
    downloadNow() {
      setTimeout(() => {
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
      }, 2000);
    }
  }
};
</script>

<style>
.corona-input {
  width: 100%;
  text-align: center;
}

.routine--template2 .routine-table th {
  padding: 6px 0;
  font-size: 22px;
}

.routine--template2 .routine-table td {
  border: 1px solid #fff;
  color: #fff;
  font-size: 20px;
  padding: 3px 0;
  text-align: center;
}
</style>
