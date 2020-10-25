<template>
    <div class="building">
        <div ref="shapediver-viewport" style="width:100%; height:400px;"></div>
        <div ref="param-controls">
            <label for="numFloors">Num Floors:</label>
            <input v-model="modelParams['Number of Floors']" type="number" step="1" id="numFloors">
            <p>Num Floors is: {{ modelParams['Number of Floors'] }}</p>

            <label for="flipStructureOrientation">Flip Structure Orientation:</label>
            <input v-model="modelParams['Flip Structure Orientation']" type="checkbox" id="flipStructureOrientation">
            <p>Flip Structure Orientation is: {{ modelParams['Flip Structure Orientation'] }}</p>

            <label for="structuralSystem">Structural System:</label>
            <select v-model="modelParams['Structural System']" id="structuralSystem">
                <option>Beams in Both Directions</option>
                <option>Beams in One Direction</option>
                <option>Beams and Girders</option>
                <option>Point Supported</option>
            </select>
            <p>Structural System is: {{ modelParams['Structural System'] }}</p>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Building',
  data() {
    return {
        modelParams: {
            "Number of Floors": 3,
            "Flip Structure Orientation": false,
            "Structural System": "Beams in Both Directions"
        }
    }
  },
  async mounted() {
    let settings = {
        showSceneMode: 1,
        container: this.$refs["shapediver-viewport"]
    }
    this.shapeDiverAPI = new window.SDVApp.ParametricViewer(settings);

    let vm = this;
    await this.shapeDiverAPI.plugins.registerCommPluginAsync({
        // ticket of the model as shown on app.shapediver.com
        ticket: vm.ticket,
        // URL of the ShapeDiver backend system used
        modelViewUrl: vm.modelViewUrl,
        // runtime id to use for this CommPlugin (you might register several)
        runtimeId: 'BuildingCommPlugin',
        // the following setting tells the viewer to wait with loading of geometry
        deferGeometryLoading: true
    });
    console.log('ShapeDiver CommPlugin successfully loaded');
    let params = await this.shapeDiverAPI.parameters.get().data;
    console.log('Available model parameters', params);
    // finally show the scene
    await this.shapeDiverAPI.plugins.refreshPluginAsync('BuildingCommPlugin');
    await this.shapeDiverAPI.updateSettingAsync('scene.show', true);
  },
  watch: {
    modelParams: { handler() { this.updateModelParams() }, deep: true }
  },
  props: ["ticket", "modelViewUrl"],
  methods: {
        updateModelParams: function() {
            let params = Object.keys(this.modelParams).map(p => ({name: p, value: this.modelParams[p]}))
            console.log("updating model params:", params)
            this.shapeDiverAPI.parameters.updateAsync(params).then(
                function(response) {
                    console.log(response);
                }
            );
        }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* CSS goes here */
</style>
