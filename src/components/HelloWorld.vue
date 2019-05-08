<template>
  <div class="">
    <p>
      name: {{ name }}
    </p>
    <p>
      user: {{ user.name }}
    </p>
    <p>
      text: {{ contents }}
    </p>
    <p>
      job: {{ job.name }}
    </p>
    <p>
      location: {{ location.name }}
    </p>
    <button @click="btn">
      button: {{ btnName }}
    </button>

    {{isTest}}

    <div>
      <div
        v-for="num in nums"
        :key="num"
      >
        {{ num }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Watch, Vue } from 'vue-property-decorator';
// import { State, Action, Getter } from 'vuex-class'

interface Location {
    id: number;
    name: string;
}

@Component
export default class HelloWorld extends Vue {
  @Prop() private value!: string;
  @Prop({ default: 'test' }) private contents: string = 'ok';
  private nums: number[] = [1, 3, 5, 7, 9];
  private user: { name: string} = { name: 'tomo' };
  private job: { id?: number; name?: string; } = {};
  private location: Location = { id: 1, name: '' };
  private btnName: string = 'button';
  // @State('isTest') private isTest: boolean = false;

  get name(): string {
    return 'taro';
  }

  private mounted(): void {
    this.job.name = 'tomoname';
    this.location.name = 'tokyo';
  }

  private btn(): void {
    this.btnName = 'clicked btn';
  }

  @Watch('btnName')
  private changed() {
    alert('changed');
  }
}
</script>

<style scoped lang="scss">
</style>
