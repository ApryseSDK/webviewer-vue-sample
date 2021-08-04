<template>
  <div id="webviewer" ref="viewer"></div>
</template>

<script>
import { ref, onMounted } from "vue";
import WebViewer from "@pdftron/webviewer";

export default {
  name: "WebViewer",
  props: { initialDoc: { type: String } },
  setup(props) {
    const viewer = ref(null);
    onMounted(() => {
      const path = `${process.env.BASE_URL}webviewer`;
      WebViewer({ path, initialDoc: props.initialDoc }, viewer.value).then(
        (instance) => {
          const { documentViewer, annotationManager, Annotations } =
            instance.Core;

          documentViewer.addEventListener("documentLoaded", () => {
            const rectangleAnnot = new Annotations.RectangleAnnotation({
              PageNumber: 1,
              // values are in page coordinates with (0, 0) in the top left
              X: 100,
              Y: 150,
              Width: 200,
              Height: 50,
              Author: annotationManager.getCurrentUser(),
            });
            annotationManager.addAnnotation(rectangleAnnot);
            annotationManager.redrawAnnotation(rectangleAnnot);
          });
        }
      );
    });
    return {
      viewer,
    };
  },
};
</script>

<style>
#webviewer {
  height: 100vh;
}
</style>
