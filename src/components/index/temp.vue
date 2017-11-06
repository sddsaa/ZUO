<template>
  <div class="article">
    <div class="header">
      <h1>推荐阅读</h1>
    </div>
    <div class="container">
      <div class="box" v-for="(hot,index) in hotarticles" :style="{backgroundImage: 'url(' + hotarticles[index].banner + ')'}">
        <div class="title">
          {{ hotarticles[index].title}}
        </div>
        <div class="text">
          {{hotarticles[index].summary}}
        </div>
        <div class="timetag">
          <div class="tag">
            {{hotarticles[index].sceneTagName}}
          </div>
          <div class="time">
            {{hotarticles[index].timeAgo}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
