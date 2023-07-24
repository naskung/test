props: {
    itemId: {
      type: Number,
      default: 0
    }
 },
  methods: {
   delQuerysToStore(item) {
       this.$emit('delete', this.itemId)
     }
   }
