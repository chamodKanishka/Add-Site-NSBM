<template>
<div>
    <FacultyHome/>
    <div class="app-dashboard shrink-medium">
        <div class="app-dashboard-body off-canvas-wrapper">
            <div id="app-dashboard-sidebar" class="app-dashboard-sidebar position-left off-canvas off-canvas-absolute reveal-for-medium" data-off-canvas>
                <div class="app-dashboard-sidebar-title-area">
                    <div class="app-dashboard-close-sidebar">
                        <h3 align="center" class="app-dashboard-sidebar-block-title">Menu</h3>
                        <!-- Close button -->
                    </div>
                    <div class="app-dashboard-open-sidebar">
                        <button id="open-sidebar" data-app-dashboard-toggle-shrink class="app-dashboard-open-sidebar-button show-for-medium" aria-label="open menu" type="button">
                            <span aria-hidden="true"><a href="#"><i class="large fa fa-angle-double-right"></i></a></span>
                        </button>
                    </div>
                </div>
                <div class="app-dashboard-sidebar-inner">
                    <ul class="menu vertical">
                        <li><router-link to="/Faculty/Events" class="active">
                            <i class="large fa fa-institution"></i><span class="app-dashboard-sidebar-text">Events</span>
                        </router-link></li>
                        <li><router-link to="/Faculty/Notices">
                            <i class="large fa fa-institution"></i><span class="app-dashboard-sidebar-text">Notices</span>
                        </router-link></li>
                        <li><router-link to="/Faculty/ContactFac">
                            <i class="large fa fa-industry"></i><span class="app-dashboard-sidebar-text">Contact Admin</span>
                        </router-link></li>
                    </ul>
                </div>
            </div>
            <div class="app-dashboard-body-content off-canvas-content" data-off-canvas-content>

                <md-content class="md-scrollbar">
                        <md-card>
                            
                        <md-card-media>
                            <img src="../../images/event.jpg" alt="People">
                        </md-card-media>

                        <md-card-header>
                            <div class="md-title">Title goes here</div>
                            <div class="md-subhead">Subtitle here</div>
                        </md-card-header>

                        <md-card-expand>
                            <md-card-actions md-alignment="space-between">
                            <div>
                                <md-button class="notes_bt">Delete</md-button>
                            </div>

                            <md-card-expand-trigger>
                                <md-button class="notes_bt">View Description</md-button>
                            </md-card-expand-trigger>
                            </md-card-actions>

                            <md-card-expand-content>
                            <md-card-content>
                                Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio itaque ea, nostrum odio. Dolores, sed accusantium quasi non, voluptas eius illo quas, saepe voluptate pariatur in deleniti minus sint. Excepturi.
                            </md-card-content>
                            </md-card-expand-content>
                        </md-card-expand>
                        </md-card>
                </md-content>
            </div>
        </div>
    </div>
    <Footer/>
</div>
</template>

<script>
    import FacultyHome from "./FacultyNavbar";
    import Footer from "../Footer";
    export default {
        name: "Events",
        components: {Footer, FacultyHome},
    }
</script>

<style scoped>
    b{
        color: #fefefe;
        margin-left: 20px;
        font-family: 'Proxima Nova', 'Helvetica Neue', Helvetica, Arial, sans-serif;
        font-size: 24px;
    }
    .active{
        font-weight: bolder;
        text-decoration: none;
    }


    .app-dashboard {
        /*height: 87vh;*/
        display: -webkit-flex;
        display: -ms-flexbox;
        display: flex;
        -webkit-flex-direction: column;
        -ms-flex-direction: column;
        flex-direction: column;
    }

    .app-dashboard-body {
        -webkit-flex: 1 1 auto;
        -ms-flex: 1 1 auto;
        flex: 1 1 auto;
        display: -webkit-flex;
        display: -ms-flexbox;
        display: flex;
    }

    .app-dashboard-sidebar {
        /*background-color: #fefefe;*/
        height: 100%;
        /*overflow-x: visible;*/
        /*overflow-y: auto;*/
        z-index: 1;
        transition: all 0.5s ease;
    }

    .app-dashboard-sidebar .app-dashboard-sidebar-inner {
        /*height: 100%;*/
        overflow-x: hidden;
        overflow-y: auto;
    }

    .reveal-for-medium .app-dashboard-open-sidebar {
        display: none;
    }

    .active{
        font-weight: bolder;
        text-decoration: none;
    }
    li span{
        font-size: larger;
    }

    .card-expansion {
    height: 480px;
  }

  .md-card {
    width: 320px;
    display: inline-block;
    vertical-align: top;
    background-color: #19589d;
    color: white;
    margin:20px;
  }

  .notes_bt{
      color:white;
  }

    .md-content {
        max-width: 1500px;
        max-height: 100vh;
        overflow: auto;
    }
</style>
