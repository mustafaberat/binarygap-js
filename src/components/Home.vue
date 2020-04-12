<template>
  <div class="container">
    <main>
      <h1 class="enter-title">Binary Gap Solution with JS</h1>
      <input
        type="number"
        name="number"
        v-model="number"
        @keyup="largestGap"
        placeholder="Enter your number"
      />
      <div v-if="binaryNumber !== ''">
        <h1 class="results">
          Input: <span class="span">{{ number }}</span>
        </h1>
        <h1 class="results">
          Converting Binary: <span class="span">{{ binaryNumber }}</span>
        </h1>
        <h1 class="results">
          Binary Gap Solution: <span class="span">{{ gapnumber }}</span>
        </h1>
      </div>
    </main>
    <div class="problem">
      <h2 class="problem-title">Problem:</h2>
      <p class="problem-desc">
        A binary gap within a positive integer N is any maximal sequence of
        consecutive zeros that is surrounded by ones at both ends in the binary
        representation of N. For example, number 9 has binary representation
        1001 and contains a binary gap of length 2. The number 529 has binary
        representation 1000010001 and contains two binary gaps: one of length 4
        and one of length 3. The number 20 has binary representation 10100 and
        contains one binary gap of length 1. The number 15 has binary
        representation 1111 and has no binary gaps. Write a function: function
        solution(N); that, given a positive integer N, returns the length of its
        longest binary gap. The function should return 0 if N doesn't contain a
        binary gap. For example, given N = 1041 the function should return 5,
        because N has binary representation 10000010001 and so its longest
        binary gap is of length 5. Assume that: N is an integer within the range
        [1..2,147,483,647].
      </p>
      <a
        class="problem-desc ref"
        href="https://github.com/mustafaberat/binarygap-js"
        >Codes...</a
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      binaryNumber: "",
      gapnumber: 0,
      number: ""
    };
  },
  methods: {
    largestGap() {
      this.binaryNumber = Math.abs(this.number).toString(2);
      let finalMax = 0,
        currentMax = 0;

      for (var i = 0; i < this.binaryNumber.length; i++) {
        if (this.binaryNumber[i] === "0") {
          currentMax += 1;
        }
        if (this.binaryNumber[i] === "1" && i != 0) {
          finalMax = Math.max(finalMax, currentMax);
          currentMax = 0;
        }
      }
      this.gapnumber = finalMax; //update final
    }
  }
};
</script>
