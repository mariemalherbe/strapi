<template>
  <div class="hello">
    <section
      v-for="home in homes"
      :to="{ path: '/homes/' + home.id }"
      class="uk-link-reset"
      :key="home.id"
    >
  <div class="landing">
    <h1>{{ home.header.header_title }}</h1>
    <h3>{{ home.header.header_description }}</h3>
  </div>
   <section class="landing2">
     <h1 class="h1_skills">{{home.skills.section_title}}</h1>
        <div class="lists">
          <div class="list" v-for="content in home.skills.section_content" :key="content">
              <h2> {{ content.Title }} </h2>
              <p>{{ content.description }}</p>
          </div>
        </div>
    </section>
  </section>
</div>

</template>

<script>
import gql from "graphql-tag";

export default {
  data() {
    return {
      homes: []
    };
  },
  apollo: {
    homes: gql`
      query Homes {
        homes {
          header{
            header_title,
            header_description
          },
          skills {
            section_title,
            section_content{
              Title,
              description
            }
          }
        }
      }
    `
  }
};
</script>

<style scoped>

.hello{
  font-family: 'Roboto', sans-serif;
}

h1{
  margin: 10px 0px;
  font-size: 5em;
  font-weight: 700;
  font-family: 'Roboto', sans-serif;
  color: #2c3e50 !important;
}

h3 {
  font-weight: 100;
  margin: 0px;
  max-width: 300px;
  margin: 0 auto;
  color: #2c3e50 !important;
  text-align: center;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.img{
  width: 25vw;
}

.landing{
  margin-bottom: 100px;
  background-color: #ffe4c4;
  padding: 60px;
  width: 80vw;
  height: 60vh;
  border-radius: 2em;
  margin: 0 100px auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.landing2{
  width: 80vw;
  border-radius: 2em;
  margin: 135px auto;
}

.lists{
  display: flex;
  margin-top: 70px;
}


.h1_skills{
  text-align: left !important;
  max-width: 45vw !important;
  line-height: 1em !important;
}

.skill_title h1{
  font-size: 1.5em !important;
}

.list{
  margin-right: 100px;
  background-color: rgb(184, 200, 245);
  color: rgb(71, 82, 129);
  padding: 50px;
  border-radius: 2em;
}

.list h2{
  color: rgb(71, 82, 129);
  text-align: center;
  font-weight: 600;
}

.list p{
  white-space: pre;
  text-align: center;
  font-weight: 300;
  margin: 0;
}
</style>

