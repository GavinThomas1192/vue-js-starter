<template>
    <div class="form-horizontal">
    <div class="form-group">
      <div class="col-sm-6">
        <label>date</label>
        <input
          type="date"
          class="form-control"
          v-model="date"
          placeholder="Date"
        />
      </div>
      <div class="col-sm-6">
        <label>hours</label>
        <input
          type="number"
          class="form-control"
          v-model="totalTime"
          placeholder="Hours"
        />
      </div>
    </div>
    <div class="form-group">
      <div class="col-sm-12">
        <label>comments</label>
        <input
          type="text"
          class="form-control"
          v-model="comment"
          placeholder="Comment"
        />
      </div>
    </div>
    <button class="btn btn-primary" @click="save()">save</button>
    <router-link to="/time-entries" class="btn btn-danger">timeEntries</router-link>
    <hr>
  </div>
</template>

<script>
    export default {
        name: 'LogTime',
        data(){
            return {
                data: '',
                totalTime: '',
                comment:''
            }
        },
        methods: {
            save() {
                const plan = {
                    name: 'test',
                    avatar:'https://sfault-avatar.b0.upaiyun.com/147/223/147223148-573297d0913c5_huge256',
                    totalTime: this.totalTime,
                    date: this.date,
                    comment: this.comment
                }
                this.$store.dispatch('savePlan', plan);
                this.$store.dispatch('addTotalTime', this.totalTime);
                this.$router.go(-1);
            }
        }
    }


</script>


