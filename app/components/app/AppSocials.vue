<template>
  <div class="app-socials">
    <a href="#" target="blank" class="app-socials__VK">
      <SvgIcon
        class="app-social__VK-icon x-btn"
        width="58"
        height="18"
        name="vk1"
      />
    </a>
    <a href="#" target="blank" class="app-socials__VK">
      <SvgIcon
        class="app-socials__VK-icon x-btn"
        width="58"
        height="18"
        name="vk2"
      />
    </a>
  </div>
</template>

<style lang="less">
.app-socials {
  display: flex;
  gap: 20px;
  align-items: center;
  justify-content: space-between;
  //   width: 100%;
  @media @bw960 {
    flex-wrap: wrap;
    justify-content: left;
  }

  &__VK {
    display: inline-block;
    margin-right: 10px;
    gap: 12px;
    white-space: nowrap;
    cursor: pointer;
  }

  &__VK-icon {
    width: 100%;
    height: 100%;
    object-fit: contain;
    @media @bw370 {
      max-width: 65px;
      height: 65px;
    }
  }
}
</style>
