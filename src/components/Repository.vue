<template>
  <div>
    <div class="card card-body mb-2">
      <div class="row">
        <div class="col-md-6">
          <a :href="repo.html_url" traget="_blank"></a>
          {{repo.name}}
        </div>
        <div class="col-md-6">
          <span class="badge badge-primary">Stars: {{repo.stargazers_count}}</span>
          <span class="badge badge-warning">Watch: {{repo.watchers_count}}</span>
          <span class="badge badge-info">Forks: {{repo.forks_count}}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["repo"]
};
</script>
