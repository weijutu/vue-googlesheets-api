<template>
  <div class="hello">
    <h2>Vue Google Sheets api 實作</h2>
    <button @click="login">讀取 Google Sheets 檔案</button>
    <br />
    <br />
    <table align="center">
      <tr v-for="record in records">
        <td v-for="r in record">{{ r }}</td>
      </tr>  
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      records: [],
    }
  },
  mounted () {
    let vm = this;
    vm.login();
  },
  methods: {
    login () {
      let vm = this;
      this.$getGapiClient()
      .then(gapi => {
        var params = {
          spreadsheetId: '1GnvjCutd-z8iYb3LrsOruRopNS7Lf2VVQ_4zBcK84TQ',
          range: 'A1:E100',
          valueRenderOption: 'FORMATTED_VALUE',
          dateTimeRenderOption: 'FORMATTED_STRING',
        };
        var request = gapi.client.sheets.spreadsheets.values.get(params)
        request.then(function(response) {
          var result = response.result;

          // this.records = result.values;
          vm.records = result.values;
          for(var i = 0; i <= vm.records.length; i++) {
            // title
            var title = vm.records[0];
            var objTitle = {};
            for(var j = 0; j<= title.length; j++) {
              objTitle = title[j]
            }
          }
        }, function(reason){
          console.error('error:', reason)
        });
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
table {
    width: 600px;
    border: 1px solid #505050;
    margin-bottom: 15px;
    color: #505050;
    border-collapse: collapse;
}

td{
    border: 1px solid #505050;
    padding: 10px;
}
</style>
