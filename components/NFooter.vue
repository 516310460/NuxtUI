<script>
import NFooterTheme from "../plugins/themes/default/NFooter";

const { baseClass } = NFooterTheme;

export default {
  name: "NFooter",

  install(Vue, theme) {
    selfInstall(Vue, theme, this);
  },

  props: {
    baseClass: {
      type: [String, Object, Array],
      default: baseClass
    }
  },
  computed: {
    /**
     * The default classes for the footer
     * 栅格的默认类
     * @return {Array}
     */
    currentClass() {
      let newSize = "";
      let classes = [
        `${this.$options._componentTag}`,
        `${this.$options._componentTag}-size-${newSize || "default"}`,
        this.baseClass
      ];

      return classes;
    }
  },
  methods: {
    onClick(e) {
      this.$emit("click", e);
    },
    /**
     * Raster attribute
     * 顶栏容器属性
     * @return {Object}
     */
    getAttributes() {
      return {
        id: this.id
      };
    }
  },
  render: function(createElement) {
    return createElement(
      "footer",
      {
        attrs: this.getAttributes(),
        class: this.currentClass,
        on: {
          click: this.onClick
        }
      },
      this.$slots.default
    );
  }
};
</script>
