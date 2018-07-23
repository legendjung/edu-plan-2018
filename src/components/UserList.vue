<template>
    <div class="container">
    <div class="col-lg-8 col-md-10 mx-auto" v-show="users.no!=''">
        <div class="form-control" style = "border : none;" v-if="users.p!=''|| users.r!='' || users.v!=''">
            <label>{{users.name}} 님의 신청 현황은 다음과 같습니다. </label>
            <div class="row">
                <table class="table">                
                    <tr v-show="users.p!=''">
                        <th> PaaS </th>
                        <td> <span v-if="users.p != ''">{{users.p}}월</span><span v-else>없음</span></td>    
                    </tr>  
                    <tr v-show="users.r!=''">                   
                        <th> Rest API </th>
                        <td> <span v-if="users.r != ''">{{users.r}}월</span> <span v-else>없음</span></td>    
                    </tr>  
                    <tr v-show="users.v!=''">
                        <th> Vue.js </th>
                        <td> <span v-if="users.v != ''">{{users.v}}월</span><span v-else>없음</span> </td>    
                    </tr>  
                </table>
            </div>  
        </div>
        <div class="form-control"  style = "border : none;" v-else>
            <label>{{users.name}} 님의 신청 현황이 없습니다.</label>
        </div>
        <br>
    </div>
    </div>
</template>

<script>
export default {
    name : "userlist",
    props: ["users"]
}
</script>

<style>

.close {
    position: relative; right: 0; top: 0;
    padding: 8px 12px 8px 12px
}
.close:hover {
    background-color: #f44336;  color: white;
}

.checked {
    background: #BBB;  color: #fff;  text-decoration:line-through;
}

.post-title .complete {
    color: black; text-decoration: none!important;
}
</style>