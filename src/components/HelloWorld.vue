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

interface Location {
    id: number;
    name: string;
}

@Component
export default class HelloWorld extends Vue {
  @Prop() private value!: string;
  @Prop({ default: 'test' }) contents!: string;
  private nums!: number[] = [1, 3, 5, 7, 9];
  private user!: {key?: string;} = {name: 'tomo'};
  private job!: {id?: number; name?: string;} = {};
  private location!: Location = {};
  private btnName: string = "button"

  get name(): string {
    return 'taro';
  }

  mounted(): void {
    console.log('mounted');
    this.job['name'] = 'tomoname';
    this.location.name = 'tokyo';
  }

  public btn(): void {
    this.btnName = "clicked btn";
  }


  @Watch('btnName')
  public changed(){
    alert("changed");
  }
}
</script>

<style scoped lang="scss">
</style>
