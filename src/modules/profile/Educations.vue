<template>
  <div class="incre-row">
    <label class="title"><b>EDUCATIONAL BACKGROUND</b></label>
    <div class="incre-row">
      <div class="rl-container-item" v-for="(item, index) in data" :key="index">
        <span class="header">
          <i class="fas fa-check" v-if="item.verified === true"></i>
          {{item.school}}
        </span>
        <span class="summary-header">
          <div>
            <i class="fas fa-calendar"></i>
            <span> 
              <label class="cards-label"> 
                {{ item.month_started }}
                {{ item.year_started }}
              </label>
              -
              <label class="cards-label" v-if="item.month_ended && item.year_ended !== null">
                {{ item.month_ended }}
                {{ item.year_ended }}
              </label>
              <label class="cards-label" v-else>
                Present
              </label>
            </span>
          </div>
          <div>
            <i class="fas fa-graduation-cap"></i>
            <span>
              {{ item.degree }}
            </span>
          </div>
          <div>
            <i class="fas fa-book"></i>
            <span>
              {{ item.field_of_study }}
            </span>
          </div>
        </span>
      </div>
    </div>
  </div>
</template>
<style scoped>
.incre-row .title{
  width: 100%;
  float: left;
  height: 50px;
  line-height: 50px;
  color: #555;
  border-top: solid 1px #ddd;
  border-bottom: solid 1px #ddd;
}

.incre-row{
  margin-bottom: 25px;
}

.bordered{
  border-top: solid 1px #ddd
}

.borderless td, .borderless th {
    border: none;
}
.rl-container-item{
  width: 50%;
  float: left;
  min-height: 50px;
  overflow-y: hidden;
  margin-top: 10px;
  padding-left: 10px;
  padding-right: 10px;
}
.rl-container-item .header{
  width: 100%;
  float: left;
  height: 40px;
  font-weight: bold;
  line-height: 50px;
  color: #555;
}

.rl-container-item .header i{
  font-size: 13px;
  padding-right: 5px;
}

.rl-container-item .summary-header i{
  padding: 0px 5px;
}

.rl-container-item .summary-header label{
  margin-bottom: 0px;
}
.rl-container-item .summary-header{
  width: 100%;
  float: left;
  line-height: 25px;
  color: #555; 
}
.rl-container-item .footer{
  width: 100%;
  float: left;
  height: 45px;
  line-height: 40px;
}
@media (max-width: 992px){
}

</style>
<script>
import ROUTER from '../../router'
import AUTH from '../../services/auth'
import CONFIG from '../../config.js'
export default{
  mounted(){
  },
  data(){
    return {
      user: AUTH.user,
      config: CONFIG
    }
  },
  props: ['data'],
  methods: {
    redirect(parameter){
      ROUTER.push(parameter)
    }
  }
}
</script>
