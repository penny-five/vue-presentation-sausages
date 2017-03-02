<script>
import ActionButton from './ActionButton.vue';
import Logo from './assets/logo.png';


const rng = max => Math.ceil(Math.random() * max);


export default {
  data() {
    return {
      showStats: true,
      numbers: []
    };
  },
  methods: {
    generateNumber() {
      this.numbers.push(rng(500));
    },
    toggleStatsVisibility() {
      this.showStats = !this.showStats;
    }
  },
  computed: {
    hasNumbers() {
      return this.numbers.length > 0;
    },
    lastFiveNumbers() {
      return this.numbers.slice(Math.max(this.numbers.length - 5, 0));
    },
    min() {
      return Math.min(...this.numbers);
    },
    max() {
      return Math.max(...this.numbers);
    },
    range() {
      return `${this.min} - ${this.max}`;
    }
  },
  render(h) {
    console.log('Render() called @', new Date().getTime());
    return (
      <div id="app">
        <img src={Logo} />
        <ActionButton text="Generate a new number" onClick={this.generateNumber}/>
        <ActionButton text="Show/hide stats" onClick={this.toggleStatsVisibility}/>
        {this.showStats && this.hasNumbers && (
          <div>
            <h2>Last 5 generated numbers</h2>
            <ul>
              { this.lastFiveNumbers.map(number => <li>{ number }</li>) }
            </ul>
            <h2>Smallest</h2>
            <p>{ this.min || '-' }</p>
            <h2>Largest</h2>
            <p>{ this.max || '-' }</p>
            <h2>Range</h2>
            <p>{ this.range || '-' }</p>
          </div>
        )}
      </div>
    );
  }
};

</script>

<style lang="scss">
@import "./assets/style";
@import "./assets/constants";

#app {
  font-family: Helvetica, Arial, sans-serif;
  text-align: center;
  color: $color-brand-secondary;
  margin-top: 60px;
}

a {
  color: $color-brand-primary;
}
</style>
