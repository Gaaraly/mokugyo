<!-- <script>
export const Tip = defineComponent({
  setup() {
    const text = $ref('text')
    const theTip = () => (<span absolute right-20 top-10 text-xl>{text}</span>)

    const lists = [theTip]

    return () => (
      <div>
        {lists.map(list => list)}
      </div>
    )
  },
})
// const theTip = h('span', {
//   ref: text,
//   class: 'absolute right-20 top-10 text-xl transition-all ease-out',
//   style: {
//     animation: 'fadeOutUp 1s ease-in-out',
//   },
// }, text)

{ /* @keyframes fadeOutUp {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: translate3d(0, -100%, 0);
    display: none;
  }
} */ }
</script> -->
