<template>
    <div id="id_sidebar_vue">
        <div style="padding: 20px 15px;cursor: pointer;">
            <i style="font-size: 25px;color: white;display: inline;margin-right: 8px;" class="fa fa-bars" aria-hidden="true"></i>
            <!--<span v-show="displayWelcome" class="option-name" v-on:click="$router.push('/dashboard')" style="font-weight: 700;">-->
                <!--My Dashboard-->
            <!--</span>-->
        </div>
        <ul style="padding: 0;margin: 0;">
            <li class="menuoption" v-for="item in menuOptions">
                <span class="verbose">{{item.verbose}}</span>
                <span class="option-name" v-on:click="$router.push(item.url)">
                    {{item.name}}
                </span>
            </li>
        </ul>
    </div>
</template>


<script>
    import {getAuthToken} from "../providers";

    export default {
        name: 'SidebarVue',
        data() {
            return {
                displayWelcome:false,
                menuOptions:[
                    {
                        name:"Language Management",
                        url: "language",
                        verbose: "LA"
                    },
                    {
                        name:"Staff Management",
                        url: "staff",
                        verbose:"ST"
                    },
                    {
                        name:"School Management",
                        url: "school",
                        verbose:"SC"
                    },
                    {
                        name:"Product Management",
                        url: "product",
                        verbose:"PR"
                    },
                    {
                        name:"Service Management",
                        url: "service",
                        verbose:"SE"
                    },
                ],
            }
        },
        beforeMount() {
            if(getAuthToken() === null) {
                this.$router.push("/");
            }
        }
    }

</script>

<style>
    #id_sidebar_vue{
        position: fixed;
        height: 100%;
        overflow-x: hidden;
        z-index: 1;
        top:0;
        left:0;
        background-color: darkcyan;
        width: 60px;
        transition: width 0.2s;
        font-family: "Dosis", "Source Sans Pro", "Helvetica Neue", Arial, sans-serif;
    }
    #id_sidebar_vue:hover{
        width: 250px;
        transition: width 0.2s;
    }
    .menuoption{
        cursor: pointer;
        list-style: none;
        color: white;
        font-size: 20px;
        padding: 20px 10px;
        overflow: hidden;
    }
    .menuoption:hover {
        background-color: #474747;
    }
    .verbose {
        padding: 5px;
        border: 2px solid white;
        border-radius: 5px;
    }
    .option-name{
        color: white;
        font-size: 16px;
        padding: 5px 0 5px 16px;
        white-space: nowrap;
    }
    .active-link{
        background-color: #474747;
        font-weight: 700;
    }
</style>