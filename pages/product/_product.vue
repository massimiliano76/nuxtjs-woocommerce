<template>
  <div>
    <ShowSingleProduct :product="product" />
  </div>
</template>

<script>
import GET_SINGLE_PRODUCT_QUERY from '@/apollo/queries/GET_SINGLE_PRODUCT_QUERY.gql'

export default {
  name: 'Product',
  layout: 'Layout',
  apollo: {
    product: {
      query: GET_SINGLE_PRODUCT_QUERY,
      prefetch: ({ id, slug }) => ({ id, slug }),
      variables() {
        return { id: this.$route.query.id, slug: this.$route.params.product }
      },
    },
  },
  transition: {
    name: 'home',
    mode: 'out-in',
  },
}
</script>
