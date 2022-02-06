<template>
  <div>
    <!-- Below is where the links start -->
    <div class="grid grid-flow-row grid-cols-12 gap-4">

        <button class="col-start-4 col-span-6 btn btn-outline text-bg-neutral-content hover:btn-bg-neutral-focus"  v-for="link in showLinks" :key="link.Box_Text">
      <div >
          <a
            :href="link.Link + '?' + current()"
            class="text-white hover:text-black"
            target="_blank"
            rel="noopener"
          >
            {{ link.Box_Text }}
          </a>

        </div>
      </button>
    </div>
    <!-- Above is where the links start -->

    <!-- Below is where bottom text is. -->
    <div class="topgrid">
      <div>
        <p><br /><br /></p>
      </div>
      <div>
        <p>
          Need to connect with us in more conventional ways?<br />
          IES Jakarta - The City Center Batavia Tower 1<br />
          8th Floor Annex - Jl. K. H. Mas Mansyur Kav 126, Jakarta 10220<br />
          Phone: <a href="tel:+6281287763988">+62 812 87763988</a>
        </p>
      </div>
    </div>
  </div>
</template>
<!-- Above is where bottom text is. -->

<!-- This script gets the JSON, breaks out the links from the colors 
and makes them useful for the page. -->

<script>
export default {
  name: 'IESLinks',
  data() {
    return {
      links: [],
    }
  },
  async fetch() {
    this.links = await fetch(
      `https://api.steinhq.com/v1/storages/6166a6bb8d29ba2379f93001/IES_Links_Page`
    ).then((res) => res.json())
  },

  computed: {
    showLinks() {
      return this.links.filter((item) => item.Show === 'TRUE')
    },
    colors() {
      return this.links.filter((item) => item.Show === 'C')
    },
  },
  methods: {
    current() {
      const ms = Date.now()
      const current = ms.toString()
      return current
    },
  },
}
</script>

<style>
body {
  font-family: 'Poppins', sans-serif;
  text-align: center;
  line-height: 1.2;
  font-size: 16px;
  font-weight: 600;
  background-color: #3d3b3c;
}

h1 {
  margin: 0px;
  font-weight: 600;
  font-size: 14px;
  line-height: 1.5;
  text-overflow: ellipsis;
  max-width: 100%;
  overflow: hidden;
}

h2 {
  padding: 0px;
  margin: 0px;
  margin-bottom: 4px;
  text-align: center;
  font-weight: 600;
  line-height: 1.5;
  font-size: 16px;
}
a {
  color: #ffffff;
  text-decoration: none;
}

.topgrid {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  -moz-box-align: center;
  color: #ffffff;
}

.topgrid > div {
  grid-column: 2;
  margin-left: 12px;
  margin-right: 12px;
  max-width: 100%;
  padding: 3px;
}

.innercolumns {
  display: grid;
  justify-content: center;
  padding: 20px;
  grid-template-columns: 45px 45px 45px 45px;
  grid-template-rows: 50px;
}

.boxtext {
  overflow-wrap: break-word;
  word-break: break-word;
  hyphens: auto;
  text-decoration: none;
  white-space: normal;
  background: rgba(0, 0, 0, 0) none repeat scroll 0% 0%;
  color: inherit;
  transition: box-shadow 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s,
    border-color 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s,
    transform 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s,
    background-color 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s;
}

.boxtext:hover {
  overflow-wrap: break-word;
  word-break: break-word;
  hyphens: auto;
  white-space: normal;
  background: rgba(0, 0, 0, 0) none repeat scroll 0% 0%;
  color: inherit;
  transition: box-shadow 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s,
    border-color 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s,
    transform 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s,
    background-color 0.25s cubic-bezier(0.08, 0.59, 0.29, 0.99) 0s;
}
.afill {
  padding: 18px;
}

img {
  max-width: 96px;
  height: auto;
  padding: 14px 6px 2px;
}
</style>

<!-- this is not in use 
<script>
export default {
    name: 'IESLinks',
    data () {
        return {
            links: []
        }
},
async fetch() {
    this.links = await fetch(
        `https://api.steinhq.com/v1/storages/6166a6bb8d29ba2379f93001/IES_Links_Page`).then(res => res.json())
  },
}
</script> -->
