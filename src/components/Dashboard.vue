<template>
    <div id="view-mcq">
        <v-expansion-panels class="dark">
            <v-expansion-panel v-for="i in ques" :key="i.quesno">
                    <v-expansion-panel-header >
                        <ul>
                            <li>Q{{i.quesno}}. {{i.ques}}</li> <br>
                            <li>(a) {{i.op1}}</li> <br>
                            <li>(b) {{i.op2}}</li> <br>
                            <li>(c) {{i.op3}}</li> <br>
                            <li>(d) {{i.op4}}</li> <br>
                        </ul>
                    </v-expansion-panel-header>
                    <v-expansion-panel-content>
                        <ul>
                            <li>Answer: {{i.ans}}</li>
                            <li>Explanation: {{i.explain}}</li>
                        </ul>
                    </v-expansion-panel-content>
                
            </v-expansion-panel>
        </v-expansion-panels>
    </div>   
</template>

<script>
import db from './firebaseinit'

export default {
  data () {
      return {
          ques: [],
          x: {
              id:""
          },
        } 
    },
    created () {
        db.collection('questions').orderBy('quesno').get().then(querySnapshot => {
            querySnapshot.forEach(doc => {
                var x = doc.data();
                x.id = doc.id;
                this.ques.push(x);
                console.log(doc.data())
            })
        })
    },
}
</script>

<style lang="scss" scoped>
    .v-expansion-panel-header {
        background: transparent;
    }
</style>
