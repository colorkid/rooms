<template>
  <header class="days-header">
    <div class="days-header__arrow days-header__arrow--left"></div>
    <div class="days-header__name">{{nameMonth}}</div>
    <div class="days-header__arrow days-header__arrow--right"></div>
  </header>
</template>
<script>

export default {
  name: 'DaysHeader',
  props: ['nameMonth']
}
</script>

<style scoped>
.days-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  height: 35px;
  background-color: #eaeaea;
}

.days-header__name {
  font-size: 16px;
  font-weight: 600;
}

.days-header__arrow {
  width: 40px;
  height: 20px;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
  cursor: pointer;
}

.days-header__arrow--right {
  background-image: url(data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8c3ZnIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDI2IDI2IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNiAyNiIgd2lkdGg9IjMycHgiIGhlaWdodD0iMzJweCI+CiAgPHBhdGggZD0iTTE2LjcsMjIuN2w5LTljMC4yLTAuMiwwLjMtMC41LDAuMy0wLjdjMC0wLjMtMC4xLTAuNS0wLjMtMC43bC05LTlDMTYuNSwzLjEsMTYuMywzLDE2LDNzLTAuNSwwLjEtMC43LDAuM2wtMS40LDEuNCAgYy0wLjQsMC40LTAuNCwxLDAsMS40bDQsNGMwLjMsMC4zLDAuMSwwLjktMC40LDAuOUgxYy0wLjYsMC0xLDAuNC0xLDF2MmMwLDAuNiwwLjQsMSwxLDFoMTYuNmMwLjQsMCwwLjcsMC41LDAuNCwwLjlsLTQsNCAgYy0wLjQsMC40LTAuNCwxLDAsMS40bDEuNCwxLjRjMC4yLDAuMiwwLjQsMC4zLDAuNywwLjNDMTYuMywyMywxNi41LDIyLjksMTYuNywyMi43eiIgZmlsbD0iIzMzMzMzMyIvPgo8L3N2Zz4K);
}

.days-header__arrow--left {
  background-image: url(data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8c3ZnIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDI2IDI2IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNiAyNiIgd2lkdGg9IjMycHgiIGhlaWdodD0iMzJweCI+CiAgPHBhdGggZD0iTTkuMywyMi43bC05LTlDMC4xLDEzLjUsMCwxMy4zLDAsMTNzMC4xLTAuNSwwLjMtMC43bDktOUM5LjUsMy4xLDkuNywzLDEwLDNjMC4zLDAsMC41LDAuMSwwLjcsMC4zbDEuNCwxLjQgIGMwLjQsMC40LDAuNCwxLDAsMS40bC00LDRDNy44LDEwLjUsOCwxMSw4LjQsMTFIMjVjMC42LDAsMSwwLjQsMSwxdjJjMCwwLjYtMC40LDEtMSwxSDguNEM4LDE1LDcuNywxNS41LDgsMTUuOWw0LDQgIGMwLjQsMC40LDAuNCwxLDAsMS40bC0xLjQsMS40QzEwLjUsMjIuOSwxMC4zLDIzLDEwLDIzUzkuNSwyMi45LDkuMywyMi43eiIgZmlsbD0iIzMzMzMzMyIvPgo8L3N2Zz4K);
}
</style>
