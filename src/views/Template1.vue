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
                <input
                  type="text"
                  v-model="r.class"
                  class="table-input"
                  @blur="r.editing = false"
                />
              </td>
              <td class="column2">
                <input
                  type="text"
                  v-model="r.subject"
                  class="table-input"
                  @blur="r.editing = false"
                />
              </td>
              <td class="column3">
                <input
                  type="text"
                  v-model="r.duration"
                  class="table-input"
                  @blur="r.editing = false"
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
.routine-container {
  width: 904px;
  height: 904px;
  max-width: 100%;
  overflow: auto;
  margin-left: auto;
  margin-right: auto;
  border: 2px solid gray;
}
.routine {
  width: 900px;
  height: 900px;
  background-image: url("/img/template1.png");
  background-size: 100% 100%;

  padding-top: 231px;
}

.date {
  margin-left: 231px;
  width: 441px;
  height: 68px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-weight: bold;
  font-size: 43px;
}

.date-input {
  max-width: 100%;
  text-align: center;
}

.table-input {
  max-width: 100%;
  text-align: center;
}

.routine-table {
  border: 2px solid #fff;
  width: 679px;
  margin-left: 114px;
  margin-top: 25px;
  border-collapse: collapse;
}

.routine-table th {
  border: 1px solid #fff;
  border-collapse: collapse;
  color: #fff;
  font-size: 22px;
  padding: 12px 0;
  text-align: center;
  font-weight: bold;
}

.routine-table td {
  border: 1px solid #fff;
  color: #fff;
  font-size: 25px;
  padding: 26px 0;
  text-align: center;
}

.column1 {
  min-width: 99px;
}

.column1 .table-input {
  max-width: 100px;
}

.column2 {
  width: 300px;
}

.column2 .table-input {
  max-width: 288px;
}

.column3 {
  width: 262px;
}

.column3 .table-input {
  max-width: 240px;
}
</style>
