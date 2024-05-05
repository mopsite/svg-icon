<script setup></script>

<template>
  <div class="app">
    <h1>Svg Icon</h1>

    <h2>1. Default</h2>
    <SvgIcon />

    <h2>2. Props - url</h2>
    <h3>local: /src/assets/svgs/alien.svg</h3>
    <SvgIcon url="/src/assets/svgs/" name="alien" />
    <h3>web: https://cn.vuejs.org/logo.svg</h3>
    <SvgIcon url="https://cn.vuejs.org/" name="logo" />

    <h2>3. Props - name</h2>
    <h3>name: star</h3>
    <SvgIcon name="solid/star" />

    <h2>4. Props - size</h2>
    <h3>size: 3em</h3>
    <SvgIcon name="solid/album" size="3em" />

    <h2>5. Props - color</h2>
    <h3>color: deepskyblue</h3>
    <SvgIcon name="solid/anchor" size="3em" color="deepskyblue" />
    <h3>duotone color: { primary: 'gold', secondary: 'maroon' }</h3>
    <SvgIcon
      name="duotone/badge-dollar"
      size="3em"
      :color="{ primary: 'gold', secondary: 'maroon' }"
    />

    <h2>6. Props - opacity</h2>
    <h3>opacity: 0.4</h3>
    <SvgIcon name="regular/aperture" size="3em" :opacity="0.4" />
    <h3>duotone opacity: { primary: 0.6, secondary: 0.2 }</h3>
    <SvgIcon
      name="duotone/balloon"
      size="3em"
      :opacity="{ primary: 0.6, secondary: 0.2 }"
    />
  </div>
</template>

<style scoped></style>
