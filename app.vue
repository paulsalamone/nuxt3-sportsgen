<script setup lang="ts">
enum Formation {
  SINGLES = "singles",
  DOUBLES = "doubles",
  TEAM = "team",
}

enum Environment {
  INDOOR = "indoor",
  OUTDOOR = "outdoor",
  WATER = "water",
}

enum CoreSport {
  BASEBALL = "baseball",
  BASKETBALL = "basketball",
  FENCING = "fencing",
  SOCCER = "soccer",
}

interface SportOptions {
  formation: Formation;
  environment: Environment;
  coreSport: CoreSport;
}

const sportOptions = reactive<SportOptions>({
  formation: Formation.SINGLES,
  environment: Environment.OUTDOOR,
  coreSport: CoreSport.FENCING,
});

// export default {
//   data() {
//     return {
//       sportOptions: <SportOptions>{
//         formation: Formation.SINGLES,
//         environment: Environment.OUTDOOR,
//         coreSport: CoreSport.FENCING,
//       },
//     };
//   },
// };
</script>

<template>
  <div>
    <Header />
    <main>
      <section>
        <div class="pickers">
          <h3>Pick formation:</h3>
          <button
            :class="sportOptions.formation === Formation.SINGLES && 'selected'"
            @click="sportOptions.formation = 'singles'"
          >
            singles
          </button>
          <button
            :class="sportOptions.formation === Formation.DOUBLES && 'selected'"
            @click="sportOptions.formation = 'doubles'"
          >
            doubles
          </button>
          <button
            :class="sportOptions.formation === 'team' && 'selected'"
            @click="sportOptions.formation = 'team'"
          >
            team
          </button>

          <h3>Pick Environment:</h3>
          <button
            :class="
              sportOptions.environment === Environment.INDOOR && 'selected'
            "
            @click="sportOptions.environment = 'indoor'"
          >
            indoor
          </button>
          <button
            :class="
              sportOptions.environment === Environment.OUTDOOR && 'selected'
            "
            @click="sportOptions.environment = 'outdoor'"
          >
            outdoor
          </button>
          <button
            :class="
              sportOptions.environment === Environment.WATER && 'selected'
            "
            @click="sportOptions.environment = 'water'"
          >
            water
          </button>
          <div class="pick-sport">
            <div>
              <h3>Pick Core Sport:</h3>
              <select @change="sportOptions.coreSport = e.target.value">
                <option value="baseball">baseball</option>
                <option value="basketball">basketball</option>
                <option value="fencing">fencing</option>
                <option value="soccer">soccer</option>
              </select>
            </div>
            <!-- <div>
            <h3>Pick secondary sport</h3>
          </div> -->
          </div>
        </div>
        <div class="submit"><button id="submit">SUBMIT</button></div>
      </section>
      <section>
        <h3>Your sport:</h3>
        <!-- <h2>{{ (formation, environment, coreSport) }}</h2> -->
        <h2>YOUR SPORT</h2>
      </section>
    </main>
  </div>
</template>

<style lang="scss">
$color1: purple;
$color2: lightpink;
$color3: lightcoral;
body {
  background-color: $color1;
  border: 2px solid black;
  height: 97vh;
  padding: 10px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

main {
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100%;
  margin: auto;
}

section {
  background-color: $color2;
  padding: 20px;
  margin: 10px;
  width: 100%;
}

.pickers {
  button,
  select {
    border: none;
    padding: 10px 20px;
    margin: 3px;
    font-size: 1.3rem;
    box-shadow: inset 2px 2px 4px rgba(0, 0, 128, 0.7);
    transition: ease 100ms;
  }
  button:hover,
  select:hover {
    background-color: $color3;
  }
  button:active {
    background-color: $color1;
  }
  .selected,
  select {
    background-color: $color1;
    color: white;
  }
}

.pick-sport {
  display: flex;

  width: auto;
  div {
    // border: 1px solid magenta;
    width: 50%;
  }
}

.submit {
  display: flex;
  justify-content: center;
  margin-top: 20px;
  border-top: 1px dotted gray;

  button {
    padding: 12px 23px;
    margin: 10px;
    font-size: 1.7rem;
    border: none;
    transition: ease 100ms;
    box-shadow: inset 2px 2px 3px $color3, 4px 4px 5px $color1;
  }

  button:hover {
    background-color: $color3;
  }
  button:active {
    background-color: $color1;
  }
}
</style>
