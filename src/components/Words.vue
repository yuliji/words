<template>
  <main id="words">
    <div class="container">
      <div class="row" id="stats">
        <div class="col-6">No. {{ idx + 1 }}; Total: {{ words.length }}</div>
      </div>
      <div class="row wide-ls" id="word_list">
        <div class="col-6">
          <audio ref="player" controls autoplay>
            <source v-bind:src="audioUrl" type="audio/mpeg" />
          </audio>
          <!-- {{ thisWord }} {{ audioUrl }} -->
        </div>
      </div>
      <div class="row">
        <div class="col-6">
          <hr class="math" />
        </div>
      </div>
      <div class="row">
        <div class="col-6">
          <input
            ref="answer"
            class="form-control"
            id="answer"
            type="text"
            size="4"
            v-model="answer"
          />
        </div>
      </div>
      <div class="row mt-1">
        <div class="col-3">
          <button v-on:click="judge" class="btn btn-primary">Submit</button>
        </div>
      </div>
      <div class="row mt-1">
        <div class="col-3">
          <button v-on:click="previous" class="btn btn-primary">Previous</button>
        </div>
        <div class="col-3">
          <button v-on:click="next" class="btn btn-primary">Next</button>
        </div>
      </div>
      <div id="result" class="row mt-2">
        <div class="col-6">
          <div v-bind:class="result_class">{{ result }}</div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "Words",
  props: {
    msg: String,
  },
  data() {
    return {
      answer: "",
      result: "",
      result_class: "green",
      timer: "",
      h: 0,
      m: 0,
      s: 0,
      idx: 0,
      words: [
        "scrambled",
        "ingredients",
        "parsley",
        "kitchen",
        "finely",
        "materials",
        "container",
        "remove",
        "fertiliser",
        "stake",
        "express",
        "emotions",
        "rhyme",
        "outback",
        "muster",
        "blast off",
        "rocket",
        "zoom",
        "towards",
        "further",
        "ice rink",
        "invite",
        "session",
        "remind",
        "wobbled",
        "cause",
        "swerve",
        "entertain",
        "Wednesday",
        "almost",
        "believe",
        "beam",
        "grant",
        "daughter",
        "grief",
        "howl",
        "freeze",
        "label",
        "figure",
        "command",
        "enemy",
        "pigeon",
        "weapon",
        "launch",

        "coast",
        "rustle",
        "murky",
        "surface",
        "shining",
        "handsome",
        "delicate",
        "jumpy",
        "appetite",
        "sardines",
        "bounce",
        "shriek",
        "chuckling",
        "whiskers",
        "nourishing",
        "different",
        "scissors",
        "remaining",
        "petals",
        "sprinkle",
        "mixture",
        "yeast",
        "knead",
        "cream",
        "yolk",
        "jungle",
        "splendid",
        "delighted",
        "vines",
        "giraffe",
        "cricket",
        "whispered",
        "straggled",
        "chirping",
        "hideout",
        "drought",
        "thirsty",
        "echidnas",
        "darted",
        "selfish",
        "several",
        "nervous",
        "pistol",
        "thumping",
        "leapt",
        "energy",
        "shrub",
        "forked",
        "vegetables",
        "leathery",
        "provide",
        "shelter",
        "tropical",
        "bare",
        "brighten",
        "browse",
        "lumbering",
        "calmly",
        "somersault",
        "desperate",
        "ripe",
        "thresh",
        "wheat",
        "ground",
        "grain",
        "unusual",
        "titbits",
        "extremely",
        "greedy",
        "hatchet",
        "bridge",
        "troll",
        "poker",
        "saucer",
        "tramp",
      ],
    };
  },
  methods: {
    judge: function () {
      let answer = this.answer.trim();
      if (answer === this.words[this.idx]) {
        this.result = "Correct!";
        this.result_class = "alert-success";
      } else {
        this.result = "Wrong!";
        this.result_class = "alert-danger";
      }
    },
    next: function () {
      if (this.idx < this.words.length - 1) {
        this.idx += 1;
        this.answer = "";
        this.result = "";
        this.result_class = "";
      }
      this.$refs.answer.focus();
    },
    previous: function () {
      if (this.idx > 0) {
        this.idx -= 1;
        this.answer = "";
      }
      this.$refs.answer.focus();
    },
  },
  computed: {
    audioUrl: function () {
      let word = this.words[this.idx];
      word = word.replace(" ", "_");
      return "audio/" + word + ".mp3";
    },

    thisWord: function () {
      return this.words[this.idx];
    },
  },
  mounted: function () {
    this.$watch("idx", () => {
      this.$refs.player.load();
    });
    this.$refs.answer.focus();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
