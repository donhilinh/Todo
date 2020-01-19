<template>
  <div id="watch-example">
    <p>
      Hãy hỏi một câu hỏi yes/no:
      <input v-model="question" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script src="https://cdn.jsdelivr.net/npm/lodash@4.13.1/lodash.min.js"></script>
<script lang="ts">
import Vue from "vue";
const axios = require('axios');
var debounce = require('lodash.debounce');
var _ = require('lodash');

export default Vue.extend({
  name: "Test1",
  data() {
    return {
      question: "",
      answer: "Không thể trả lời nếu bạn chưa đặt câu hỏi!"
    };
  },
  watch: {
    // bất cứ lúc nào câu hỏi thay đổi, hàm bên dưới sẽ chạy
    question: function(newQuestion, oldQuestion) {
      this.answer = "Đang chờ bạn đặt xong câu hỏi...";
      this.getAnswer();
    }
  },
  methods: {
    // _.debounce là một hàm do Lodash cung cấp
    // Để tìm hiểu rõ hơn cách hoạt động của hàm này,
    // bạn có thể truy cập: https://lodash.com/docs#debounce
    getAnswer: _.debounce(
      function() {
        if (this.question.indexOf("?") === -1) {
          this.answer = 'Câu hỏi thì thường chứa một dấu "?" ;-)';
          return;
        }
        this.answer = "Đang suy nghĩ...";
        var vm = this;
        axios.get("https://yesno.wtf/api")
          .then(function(response) {
            vm.answer = _.capitalize(response.data.answer);
          })
          .catch(function(error) {
            vm.answer = "Lỗi! Không thể truy cập API. " + error;
          });
      },
      // Đây là thời gian (đơn vị mili giây) chúng ta đợi người dùng dừng gõ.
      500
    )
  }
});
</script>