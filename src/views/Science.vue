<template lang="">
  <br/>
  <!-- <div class="embed-responsive embed-responsive-16by9">
  <video controls="false" class="embed-responsive-item" src="https://dsqqu7oxq6o1v.cloudfront.net/preview-24051OJfY1pq7bB.mp4" allowfullscreen></video>
</div> -->
<router-view></router-view>
<bs8/>
<bs9/>



<br/>
<div class="container-fluid">
        <div class="container">
            <div class="row">
                <div class="col-lg-8">
                    <div class="row">
                  
                  
                 
                   <bs5/>
                  
                    
                 <!-- <bs6/> -->
                 <bs10/>
                   <bs11/>
                  </div>
                    </div>
             <div class="col-lg-4">
             
                    <bs7/>
                
                  </div>
            </div>
        </div>
    </div>
   
    
    
    
    
    <div class="container">
    <div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src=" https://www.youtube.com/embed/5EB1O86fhdI?si=igBixE9NQbdQww0O" allowfullscreen></iframe>
    </div>
  </div>
    <bs16/>
    
   
    <!-- <bs12/>
    <bs15/> -->
   
    
  
     
    <bs14/>
   
    </template>
    <script>
    
    import bs5 from '../components/Science/bs5.vue'
    import bs6 from '../components/Science/bs6.vue'
    import bs7 from '../components/Science/bs7.vue'
    import bs8 from '../components/Science/bs8.vue'
    import bs10 from '../components/Science/bs10.vue'
    import bs11 from '../components/Science/bs11.vue'
    import bs16 from '../components/Science/bs16.vue'
    import bs9 from '../components/Science/bs9.vue'
    import bs14 from '../components/Science/bs14.vue'
    import bs12 from '../components/Science/bs12.vue'
    import bs15 from '../components/Science/bs15.vue'

    export default {
      components:{
    bs5,bs6,
    bs8,
    bs7,
    bs10,
    bs11,
    bs9,
    bs14,
    bs12,
    bs16,
   
    bs15,
   
      },
      data() {
        return {
          articles: [],       
          currentPage: 1,    
          totalPages: 1,     
          rows: 12,          
        };
      },
      computed: {
        paginatedArticles() {
         
          const start = (this.currentPage - 1) * this.rows;
          const end = start + this.rows;
          return this.articles.slice(start, end);
        },
      },
      methods: {
        async getData() {
          // Fetch articles from the News API
          const apiKey = '1fb27fc9978d48ecadb4bdc77705325e';
          const pageSize = 100;
          
          try {
            const response = await fetch(
              `https://newsapi.org/v2/top-headlines?category=technology&language=en&apiKey=${apiKey}&pageSize=${pageSize}`
            );
            const data = await response.json();
            return data.articles;
          } catch (error) {
            console.error('Error fetching news:', error);
            return [];
          }
        },
        async fetchNews() {
         
          const articles = await this.getData();
          this.articles = articles;
          this.totalPages = Math.ceil(articles.length / this.rows);
        },
        nextPage() {
         
          if (this.currentPage < this.totalPages) {
            this.currentPage++;
          }
        },
        prevPage() {
         
          if (this.currentPage > 1) {
            this.currentPage--;
          }
        },
      },
      mounted() {
       
        this.fetchNews();
      },
    };
    </script>
    <style lang="scss" scoped>
    .page-numbers{
      margin-top: 20px;
    }
    a{
      text-decoration: none;
      color: black;
    }
      a:hover{
        text-decoration: underline;
      } 
      .next-bt,.prev-bt{
              margin: 13px;
              background-color:white;
              color: rgb(248, 2, 2);
              box-shadow: 0 0 20px 0 rgb(0 0 0 / 50%);
              border-radius: 2px;
              padding: 7px;
              font-weight: bold;
              
            }
            .next-bt:hover,.prev-bt:hover{
              background-image: linear-gradient(to right,#040d1d, #053684);
              color: white;
              
              
          
            } 
            .card{
              box-shadow: 0 0 20px 0 rgb(0 0 0 / 50%);
            }
    </style>