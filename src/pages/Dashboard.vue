<template>
    <div>
        <sidebar-vue></sidebar-vue>
        <div id="id_dashboard_vue" class="container-fluid">
            <!--<div>This is our new dashboard</div>-->
            <!--<div>{{user.full_name}}</div>-->
            <!--<div>{{user.email}}</div>-->
            <!--<div>{{user.mobile}}</div>-->
            <!--<div>{{user.permissions}}</div>-->
            <!--<div>{{user.is_admin}}</div>-->
        </div>
    </div>
</template>

<script>

    import {getAuthToken, getAdminProfile} from "../providers";
    import SidebarVue from "../components/Sidebar.vue";
    export default {
        components: {SidebarVue},
        name:'DashboardVue',

        data() {
            return {
                user:{}
            }
        },

        beforeMount() {
            if(getAuthToken() === null) {
                this.$router.push("/");
            }
            else {
                let self = this;
                getAdminProfile().then((response)=>{
                    console.log("Response: ", response.data);
                    self.user = response.data;
                })
            }
        }
    }

</script>