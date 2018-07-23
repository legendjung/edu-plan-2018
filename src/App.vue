<template>
    <div class="modal">
        <div class="form">
            <h2 id="test">금융실행그룹</h2>
            <h4 class="heading" id="test">직무현장교육 신청현황</h4>
            <h4 id="test">
                <input type="text" name="id" placeholder="사번을 입력하세요." v-model ="searchId" style="width: 250px;" @keyup.enter ="searchUser(searchId)">
                <input type="button" style="width: 100px;" class="btn btn-success" value="조회" @click="searchUser(searchId)"/>
            </h4>
            <user-list :users="resultUser"></user-list>
            <div class="row">
                <component :is="currentVue"></component>
            </div>
        </div>
        <div class="form" style="display:">
            <h2 id="test">과정 소개</h2>
            <br>
            <h3 id="test">PaaS</h3>
            <h6>*AWS, Google Cloud Platform 등의 상용 클라우드 서비스를 활용하여 PaaS에 대해 학습하는 과정입니다. docker, autoscaling, load balancing에 대한 개념을 학습하고 이를 적용해 봅니다.</h6>
            <img style="float:left" width="250px" height="150px" src="./assets/aws.png">
            <img width="250px" height="150px" src="./assets/gcp.png">
            <br><br>
            <hr>
            <br><br>
            <h3 id="test">Rest API</h3>
            <h6>*Rest API에 대한 개념과 적용을 실습해보는 과정입니다. Springboot를 활용하여 front/back-end를 직접 개발하고 학습합니다.</h6>
            <img style="float:left" width="200px" height="120px" src="./assets/restapi.jpg">
            <img width="300px" height="150px" src="./assets/spring.png">
            <br><br>
            <hr>
            <br><br>
            <h3 id="test">Vue.js</h3>
            <h6>*오픈소스 UI프레임워크 중 하나인 Vue.js에 대해 학습합니다. directive, component, webpack, vuex, vue-router 등에 대한 개념을 실습을 통해 이해하고 학습합니다.</h6>
            <img style="float:left" width="150px" height="120px" src="./assets/vue.png">
            <img width="200px" height="150px" src="./assets/javascript.jpg">
            <img width="200px" height="150px" src="./assets/nodejs-expressjs.jpg">
            <br><br>
        </div>
    </div>
</template>

<script>
import UserList from "./components/UserList.vue";
import DetailPlan from "./components/DetailPlan.vue";
import list from "./list.json";

export default {
    name: "app",
    components: { UserList, DetailPlan },
    data() {
        return {
            searchId : "",
            resultUser : { no:"" },
            currentVue : "detail-plan"
        }
    },
    methods: {
        searchUser: function(id){
            var searchkey = Number(id);
            if(id.trim()==="") {
                alert("사번을 입력해주십시오.")
            }else if(id.length > 7 ||id.length <5 ||Number.isNaN(searchkey)){
                alert("사번이 올바르지 않습니다. 다시 한 번 확인해 주십시오.")
                this.searchId = "";
            }else{
                for (var i of list) {
                    if(id===i.no) {
                        this.resultUser = i;
                        this.currentVue = null;
                        break;
                    }
                }
            }
        }
    }
}
</script>

<style scoped>
@import url("css/todoapp.min.css");
#test {
  text-align: center;
  align-content: center;
}
.img {
    float:left;
}
</style>
