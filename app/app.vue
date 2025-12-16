<template>
  <div>
    <h1>Mvp</h1>
    <img v-if="imageUrl" :src="imageUrl" alt="wunderbaum">
  </div>
</template>

<script setup>
const supabase = useSupabaseClient()

const { data } = await useAsyncData('wunderbaum-image', async () => {
  const { data } = await supabase
    .storage
    .from('files')
    .getPublicUrl('wunderbaum.png')
  return data.publicUrl
})

const imageUrl = data.value
</script>