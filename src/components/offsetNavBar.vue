<template>
    <div class="offset-navbar-container">
        <!-- left offset navbar -->
        <span class="outer-cercule">
            <span class="insile-cercule">
            </span>
        </span>
        <h1 class="company-name" :class="{'dark-text': theme == 'dark'}">
            Hiro
        </h1>
        <div class="offset-links">
            <div>
                <i class="fa-solid fa-house"></i>
                Home
            </div>
            <div>
                <i class="fa-regular fa-square-check"></i>
                My Tasks
            </div>
            <div>
                <i class="fa-solid fa-trophy"></i>
                Goals
            </div>
            <div>
                <i class="fa-solid fa-user-group"></i>
                Members
            </div>
        </div>
        <hr class="links-dividor">
        <div class="offset-workspaces">
            <div>
                WORKSPACE
                <i class="fa-regular fa-square-plus"></i>
            </div>
            <div>
                <i class="fa-solid fa-circle"></i>
                Hikoko Design
            </div>
            <div>
                <i class="fa-solid fa-circle website"></i>
                Website Design
            </div>
            <div>
                <i class="fa-solid fa-circle mobile"></i>
                Mobile Design
            </div>
            <div>
                <i class="fa-solid fa-circle blank"></i>
                Blank
            </div>
        </div>
        <!-- themes button start -->
        <div class="theme-toggle-btn-container">
            <div class="theme-toggle-btn">
                <span class="theme" :class="{'active-theme': theme == 'light'}" @click="toggleTheme('light')">
                    <i class="fa-solid fa-sun"></i>
                    Light
                </span>
                <span class="theme" :class="{'active-theme': theme == 'dark'}" @click="toggleTheme('dark')">
                    <i class="fa-regular fa-moon"></i>
                    Dark
                </span>
            </div>
        </div>
        <!-- themes button end -->
    </div>
</template>

<script>

export default{
    name: 'offsetNavBar',
    data()
    {
        return{
            theme: 'light',
        }
    },
    mounted()
    {
        //fetching user theme from local storage
        this.theme = window.localStorage.getItem("theme")
    },
    methods:
    {
        toggleTheme(theme)
        {
            // theme main functionality by assigning theme in local storage for using globaly
            this.theme = theme
            window.localStorage.setItem("theme",theme)
            window.location.reload()
        }
    }
}
</script>

<style>
    .offset-navbar-container
    {
        float: left;
        width: 20%;
        border-right: 2px solid rgba(119, 115, 115, 0.204);
        padding-bottom: 1px;
        height: 100vh;
    }

    .outer-cercule,.insile-cercule
    {
        width: 10px;
        display: inline-block;
        border-radius: 50%;
        height: 10px;
    }

    .outer-cercule
    {
        border:3px solid #306bff;
        padding: 5px;
        margin-left: 24px;
        margin-right: 10px;
    }

    .insile-cercule
    {
        border-bottom: 5px solid #c591ff;
    }

    .company-name
    {
        display: inline-block;
        margin-bottom: 0.7em;
        cursor: pointer;
    }

    .offset-links
    {
        border-top: 2px solid rgba(119, 115, 115, 0.204);
        padding: 8% 0 0 6%;
        color: #91a1b6;
    }

    .fa-user-group,.fa-trophy,.fa-square-check,.fa-house
    {
        margin-right: 10px;
    }

    .offset-links div:has(i)
    {
        margin-bottom: 20px;
        cursor: pointer;
    }

    .links-dividor
    {
        width: 90%;
        background-color: rgba(119, 115, 115, 0.204);
        border: none;
        height: 1px;
    }

    .theme-toggle-btn-container
    {
        display: flex;
        justify-content: flex-end;
        flex-direction: column;
        align-items: center;
        height: 35vh;
    }

    .theme-toggle-btn
    {
        background: #f2f4f7;
        padding: 5px;
        border-radius: 20px;
        margin-bottom: 5px;
        width: 12%;
        display: flex;
        justify-content: space-between;
        color: #91a1b6;
        position: fixed;
    }

    .theme
    {
        width: 45%;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        transition: all 0.2s ease-in-out;
    }

    .active-theme
    {
        border-radius: 20px;
        background-color: white;
        color: #1e293b;
        display: flex;
        width: 60%;
        justify-content: center;
        align-items: center;
        margin: 0 0px;
        padding: 8px 0;
        transition: all 0.2s ease-in-out;
    }

    .offset-workspaces
    {
        padding: 8% 8% 0 6%;
        color: #91a1b6;
    }

    .offset-workspaces div:first-of-type
    {
        display: flex;
        justify-content: space-between;
        margin-bottom: 20px;
    }    

    .offset-workspaces div:has(.fa-circle)
    {
        color: #1e293b;
        display: flex;
        align-items: center;
        margin-bottom: 20px;
    }

    .fa-circle
    {
        font-size: 10px;
        margin-right: 10px;
        color: #ffb57f;
    }

    .fa-circle.website
    {
        color: #306bff;
    }

    .fa-circle.mobile
    {
        color: #78c552;
    }

    .fa-circle.blank
    {
        color: #bb7fff;
    }


    /* dark theme classes */
    .dark-background
    {
        background-color: black !important;
    }

    .dark-text
    {
        color: white !important;
    }

    .dark-background ::placeholder
    {
        color: white !important;
    }

    .dark-border
    {
        border: 1px solid white !important;
    }
</style>
