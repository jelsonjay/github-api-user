<template>
  <div>
    <div class="row">
      <div class="col-md-4">
        <div class="card" style="width: 321px;">
          <img calss="card-img-top" :src="user.avatar_url" style="width: 320px;" alt="Avatar" />
          <lu class="list-group list-group-flush">
            <li class="list-group-item">
              Repositories:
              <span class="bodge badge-success">{{user.public_repos}}</span>
            </li>
            <li class="list-group-item">
              Following:
              <span class="bodge badge-primary">{{user.following}}</span>
            </li>
            <li class="list-group-item">
              Followers:
              <span class="bodge badge-info">{{user.followers}}</span>
            </li>
          </lu>
          <div class="card-body">
            <a :href="user.html_url" class="btn btn-success btn-block">See Perfil</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["user"]
};
</script>
