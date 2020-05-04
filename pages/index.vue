<template>
  <div class="container">
    <div>
      <!-- {{ users[0].id}}, {{ users[0].name}} -->
      <ul>
          <li v-for="user in users">
              {{ user.id }}, {{ user.name }}, {{ user.company.name }}
          </li>
      </ul>
      <img src="~/assets/monster06.png">
    </div>
    <div>
        <p>{{ $store.state.message }}</p>
    </div>
  </div>
</template>

<script>
const axios = require('axios')
let url = 'https://jsonplaceholder.typicode.com/users'

export default {
    asyncData({ params, error}) {
        return axios.get(url)
        .then((res) => {
            return { users: res.data }
        })
        .catch((e =>  {
            //console.log(e.response.status)
            error({ users: e.response.status, message: "エラーです"})
        }))
        }
    }

</script>