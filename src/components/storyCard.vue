<template>
    <div class="story-card" :class="{'dark-themed-card': theme == 'dark'}" draggable="true">
        <!-- using theme in styling -->
        <div class="card-sections-dividor">
            <h3 class="task-name">
                UX Adjustments
            </h3>
            <p class="task-description">
                It just needs to adaptthe UI from what you did before.
            </p>
            <div class="task-tags-container">
            <span class="task-tag">
                Research
            </span>
            <span>
                <img src="../assets/favpng_avatar-user-software-developer.png" alt="asignee img" class="asignee-img"/>
                <img src="../assets/favpng_avatar-user-software-developer.png" alt="asignee img" class="asignee-img"/>
            </span>
            </div>
        </div>
        <div class="task-comments-container">
            <i class="fa-regular fa-comment-dots"></i> 
            3
        </div>
    </div>
</template>

<script>

export default{
    name: 'storycard',
    data()
    {
        return{
            theme: null,
        }
    },
    mounted()
    {
        //fetching user theme from local storage
        this.theme = window.localStorage.getItem("theme")
    }
}
</script>

<style>
    .story-card
    {
        border-radius: 8px;
        border: 2px solid rgba(119, 115, 115, 0.204);
        margin-bottom: 30px;
        cursor:move;
    }

    .dark-themed-card
    {
        background-color: white;
    }

    .asignee-img
    {
        width: 25px;
        height: 25px;
        border-radius: 50%;
    }

    .task-name
    {
            
        margin-top: 0;
    }

    .task-description
    {
        color: #91a1b6;
        font-size: 14px;
    }

    .task-tags-container
    {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .task-tag
    {
        border-radius: 4px;
        background-color: #8a2be229;
        color: #8a2be2b3;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 5px 8px;
    }

    .asignee-img
    {
        margin-left: -6px;
        border-radius: 50%;
        border: 2px solid white;
    }

    .card-sections-dividor
    {
        border-bottom: 2px solid rgba(119, 115, 115, 0.204);
        padding: 20px 15px;
    }

    .task-comments-container
    {
        padding: 20px 15px;
        display: flex;
        color: #91a1b6;
        align-items: center;
    }

    .fa-comment-dots
    {
        margin-right: 10px;
    }
</style>