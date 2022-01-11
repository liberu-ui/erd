<script>
import { debounce } from 'lodash';
import { ResizeSensor } from 'css-element-queries';

export default {
    name: 'Erd',

    props: {
        debounce: {
            type: Number,
            default: 1,
        },
    },

    data: () => ({
        width: null,
        height: null,
        erd: null,
    }),

    mounted() {
        this.erd = new ResizeSensor(this.$el, debounce(el => {
            this.width = el.width;
            this.height = el.height;
        }), this.debounce);
    },

    beforeUnmount() {
        this.erd = null;
    },

    render() {
        return this.$slots.default({
            width: this.width,
            height: this.height,
        });
    },
};
</script>
