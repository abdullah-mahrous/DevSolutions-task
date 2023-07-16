<template>
  <!-- fixed buttons -->
  <div class="fixed-btn new-task">
    <i class="fa-regular fa-square-plus"></i>
    New Task
  </div>
  <div class="fixed-btn color-btn">
    <i class="fa-solid fa-circle"></i>
    <i class="fa-solid fa-circle website"></i>
    <i class="fa-solid fa-circle blank"></i>
    <i class="fa-solid fa-circle mobile"></i>
  </div>
  <!-- navigation start -->
  <div class="navigation-container">
    <OffsetNavBar/>
    <NavBar/>
  </div>
    <!-- navigation end -->
    <!-- details section start -->
  <div class="workspace-details">
    <p class="workspace-path">
      Workspace / Hikoko Design / Board
    </p>
    <div class="workspace-actions-wraper">
      <h2 class="workspace-name" :class="{'dark-text': theme == 'dark'}">
        Hikoko Design
      </h2>
      <div>
        <span class="btn-container" :class="{'dark-text dark-border': theme == 'dark'}">
          <i class="fa-solid fa-bolt"></i>
        </span>
        <span class="btn-container" :class="{'dark-text dark-border': theme == 'dark'}">
          <i class="fa-regular fa-star"></i>
        </span>
        <span class="btn-container" :class="{'dark-text dark-border': theme == 'dark'}">
          <i class="fa-solid fa-user-group"></i>
          Share
        </span>
      </div>
    </div>
    <div class="members-container">
      <span class="members-imgs-container">
        <img src="./assets/favpng_avatar-user-software-developer.png" alt="user img" class="member-img">
        <img src="./assets/favpng_avatar-user-software-developer.png" alt="user img" class="member-img">
        <img src="./assets/favpng_avatar-user-software-developer.png" alt="user img" class="member-img">
        <img src="./assets/favpng_avatar-user-software-developer.png" alt="user img" class="member-img">
        <span class="other-members">
          +6
        </span>
      </span>
      <span class="btn-container" :class="{'dark-text dark-border': theme == 'dark'}">
        Only My
      </span>
    </div>
  </div>
    <!-- details section end -->
    <!-- stories section start -->
  <section class="workspace-details">
    <div class="stories-column">
        <div class="story-details">
          <div>
            <h4 class="story-name" :class="{'dark-text': theme == 'dark'}">
              TODO
            </h4>
            <span class="tasks-number" :class="{'dark-text dark-border': theme == 'dark'}">
              2
            </span>
          </div>
          <i class="fa-solid fa-ellipsis" :class="{'dark-text': theme == 'dark'}"></i>
        </div>
        <hr class="column-color" :class="{'dark-dividor dark-border': theme == 'dark'}"/>
        <!-- card component place -->
        <StoryCard/>
        <StoryCard/>
        <StoryCard/>
    </div>
    <div class="stories-column">
        <div class="story-details">
          <div>
            <h4 class="story-name" :class="{'dark-text': theme == 'dark'}">
              IN WORK
            </h4>
            <span class="tasks-number" :class="{'dark-text dark-border': theme == 'dark'}">
              4
            </span>
          </div>
          <i class="fa-solid fa-ellipsis" :class="{'dark-text': theme == 'dark'}"></i>
        </div>
        <hr class="column-color in-work-color"/>
        <!-- card component place -->
        <StoryCard/>
        <StoryCard/>
    </div>
    <div class="stories-column">
        <div class="story-details">
          <div>
            <h4 class="story-name" :class="{'dark-text': theme == 'dark'}">
              QA
            </h4>
            <span class="tasks-number" :class="{'dark-text dark-border': theme == 'dark'}">
              8
            </span>
          </div>
          <i class="fa-solid fa-ellipsis" :class="{'dark-text': theme == 'dark'}"></i>
        </div>
        <hr class="column-color qa-color"/>
      <!-- card component place -->
      <StoryCard/>
    </div>
    <div class="stories-column">
        <div class="story-details">
          <div>
            <h4 class="story-name" :class="{'dark-text': theme == 'dark'}">
              COMPLETED
            </h4>
            <span class="tasks-number" :class="{'dark-text dark-border': theme == 'dark'}">
              3
            </span>
          </div>
          <i class="fa-solid fa-ellipsis" :class="{'dark-text': theme == 'dark'}"></i>
        </div>
        <hr class="column-color completed-color"/>
      <!-- card component place -->
    </div>
  </section>
</template>

<script>
import NavBar from './components/navBar.vue'
import OffsetNavBar from './components/offsetNavBar.vue'
import StoryCard from './components/storyCard.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    OffsetNavBar,
    StoryCard
  },
  data()
  {
    return{
      theme: null,
      cards: [],
      columns: [],
    }
  },
  mounted()
  {
    //fetching user theme from local storage
    this.theme = window.localStorage.getItem("theme");
    
    //asigning dark background to html body
    if(this.theme == 'dark')
      document.getElementsByTagName("body")[0].classList.add("dark-background");
    else
      document.getElementsByTagName("body")[0].classList.remove("dark-background");

    //fetching all cards and stories columns in arrays
    this.cards = document.querySelectorAll(".story-card");
    this.columns = document.querySelectorAll(".stories-column");
    let dragedCard = null;

    //loping over cards to assign the draged item and add opacity effect
    this.cards.forEach(card =>{
      card.addEventListener("dragstart",()=>{
        dragedCard = card;
        card.style.opacity = "0.5";
      })

      card.addEventListener("dragend",()=>{
        dragedCard = null;
        card.style.opacity = "1";
      })
    })

    //preventing draging default nodrag
    this.columns.forEach(column =>{
      column.addEventListener("dragover",(e)=>{
        e.preventDefault();
      })

      //using drop event to add child
      column.addEventListener("drop",()=>{
        column.append(dragedCard)
      })
    })
  }
}
</script>

<style>
  body
  {
    padding: 0;
    margin: 0;
  }

  .member-img
  {
    width: 35px;
    height: 35px;
    border: 3px solid white;
    margin-right: -6px;
    border-radius: 50%;  
  }

  .workspace-details
  {
    width: 76%;
    float: right;
    margin-bottom: 2%;
  }

  .workspace-path
  {
    color: #91a1b6;
    font-size: 14px;
  }

  .workspace-name
  {
    color: #1e293b;
    font-size: 30px;
  }

  .btn-container
  {
    border: 1px solid rgba(119, 115, 115, 0.204);
    padding: 10px;
    font-size: 16px;
    border-radius: 8px;
    margin-right: 8px;
    cursor: pointer;
  }

  .workspace-actions-wraper
  {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .workspace-name + div
  {
    margin-right: 20px;
  }

  .other-members
  {
    width: 35px;
    height: 35px;
    display: inline-flex;
    justify-content: center;
    border-radius: 50%;
    align-items: center;
    background: #eaf0ff;
    font-size: 14px;
    color: #91a1b6;
    border: 3px solid white;
  }

  .members-imgs-container
  {
    display: inline-flex;
    margin-right: 20px;
  }

  .members-container
  {
    display: flex;
  }

  section.workspace-details
  {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    width: 75%;
    margin-right: 1%;
  }

  .story-name
  {
    color: #1e293b;
    display: inline-block;
    margin-right: 12px;
  }

  .story-details
  {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 35px;
  }

  .tasks-number
  {
    display: inline-flex;
    justify-content: center;
    align-items: center;
    width: 30px;
    height: 20px;
    border-radius: 20px;
    color: #91a1b6;
    font-size: 14px;
    border: 1px solid rgba(119, 115, 115, 0.204);
  }

  .column-color
  {
    height: 0.5px;
    border: 1px solid;
    background: black;
    margin-bottom: 30px;
  }

  .dark-dividor
  {
    background-color: white !important;
  }

  .stories-column
  {
    margin: 0px 5% 8% 0;
  }

  .in-work-color
  {
    background-color: #2e69ff;
    border: 1px solid #2e69ff;
  }

  .qa-color
  {
    background-color: #ffb47e;
    border: 1px solid #ffb47e;
  }

  .completed-color
  {
    background-color: #76c450;
    border: 1px solid #76c450;
  }

  .fixed-btn
  {
    position: fixed;
    bottom: 5%;
    height: 40px;
    right: 10%;
    padding: 0 15px;
  }

  .new-task
  {
    background-color: #2e69ff;
    color: white;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .fa-square-plus
  {
    margin-right: 5px;
  }

  .color-btn
  {
    right: 5%;
    border-radius: 50%;
    width: 3%;
  }
</style>
