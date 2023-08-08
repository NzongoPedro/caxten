<template>
  <div class="mt-5">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <div class="card text-center">
            <div class="card-header">
              <div class="mt-3 alert">
                <a
                  href="#!"
                  class="btn btn-sm btn-primary border-1 rounded rounded-circle"
                  @click="page = page > 1 ? page - 1 : page"
                >
                  <i class="bi bi-arrow-left-short"></i>
                </a>
                {{ page }} / {{ pages }}
                <a
                  class="btn btn-sm btn-primary border-1 rounded rounded-circle"
                  @click="page = page < pages ? page + 1 : page"
                >
                  <i class="bi bi-arrow-right-short"></i>
                </a>
                |
                <a
                  href="#!"
                  class="btn btn-sm btn-primary border-1 rounded rounded-circle"
                  @click="rotation = rotation - 90"
                >
                  <i class="bi bi-arrow-90deg-left"></i>
                </a>
                {{ rotation }}º
                <a
                  class="btn btn-sm btn-primary border-1 rounded rounded-circle"
                  @click="rotation = rotation + 90"
                >
                  <i class="bi bi-arrow-90deg-right"></i>
                </a>
                |
                <a
                  href="#!"
                  class="btn btn-sm btn-primary border-1 rounded rounded-circle"
                  @click="scale = scale > 0.25 ? scale - 0.25 : scale"
                >
                  <i class="bi bi-zoom-out"></i>
                </a>
                {{ scale * 100 }}%
                <a
                  href="#!"
                  class="btn btn-sm btn-primary border-1 rounded rounded-circle"
                  @click="scale = scale < 2 ? scale + 0.25 : scale"
                >
                  <i class="bi bi-zoom-in"></i>
                </a>
              </div>
            </div>
            <div class="card-body">
              <section class="frame text-center ml-5">
                <VuePDF
                  :pdf="pdf"
                  :page="page"
                  :rotation="rotation"
                  :scale="scale"
                  annotation-layer
                  size="800"
                  height="800"
                />
              </section>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import { VuePDF, usePDF } from "@tato30/vue-pdf";

const page = ref(1);
const rotation = ref(0);
const scale = ref(3);
const { pdf, pages } = usePDF("./pdf/1.pdf");
</script>