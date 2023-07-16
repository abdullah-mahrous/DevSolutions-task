<template>
  <nav class="top-navbar">
    <!-- top navbar -->
    <div class="left-links-container">
        <span>
            <i class="fa-solid fa-list"></i>
            List
        </span>
        <span>
          <i class="fa-solid fa-chart-simple"></i>
            Board
        </span>
        <span>
          <i class="fa-solid fa-calendar-days"></i>
            Calendar
        </span>
    </div>
    <div class="right-links-container">
      <div class="search-container">
        <i class="fa-solid fa-magnifying-glass"></i>
        <input type="search" placeholder="Search..." class="search-input" :class="{'dark-background dark-text': theme == 'dark'}"/>
      </div>
        <span>
          <i class="fa-regular fa-comment-dots"></i>
        </span>
        <span>
          <i class="fa-regular fa-bell"></i>
        </span>
          <img src="../assets/favpng_avatar-user-software-developer.png" alt="user img" class="user-profile-img"/>
    </div>
  </nav>
</template>

<script>

export default{
  name: 'topNavBar',
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
  .top-navbar
  {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5% 2%;
    border-bottom: 2px solid rgba(119, 115, 115, 0.204);
    margin-bottom: 2%;
  }

  .left-links-container,.right-links-container
  {
    display: flex;
    justify-content: space-between;
    color: #91a1b6;
    font-size: 16px;
    align-items: center;
    width: 24%;
  }

  .right-links-container
  {
    width: 28%;
  }

  .left-links-container span,.right-links-container span
  {
    cursor: pointer;
  }

  .fa-calendar-days,.fa-chart-simple,.fa-list
  {
    margin-right: 8px;
  }

  .search-container
  {
    border: 1px solid rgba(119, 115, 115, 0.4);
    display: flex;
    align-items: center;
    border-radius: 24px;
    padding: 8px 8px 8px 12px;
    width: 38%;
  }

  .search-input
  {
    border: none;
    width: 100%;
  }

  .search-input:focus-visible
  {
    outline: none;
  }

  .fa-magnifying-glass
  {
    color: dodgerblue;
    margin-right: 5px;
  }

  .user-profile-img
  {
    width: 35px;
    height: 35px;
    cursor: pointer;
  }

  .fa-chart-simple
  {
    rotate: 180deg;
  }

  .fa-bell,.fa-comment-dots
  {
    font-size: 18px;
  }
</style>