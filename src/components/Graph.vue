<template>
  <div class="canvasWrap">
    <canvas id="chart"></canvas>
  </div>
</template>

<script>
import Chart from 'chart.js';
import data from '@/assets/data';

const drawGraph = () => {
  const myLabels = [];
  const myData = [];

  for (let i = 0; i < data.length; i += 1) {
    myLabels.push(data[i].date);
    myData.push(data[i].visits);
  }

  const ctx = document.getElementById('chart').getContext('2d');
  const chart = new Chart(ctx, {
    type: 'line',
    data: {
      labels: myLabels,
      datasets: [{
        label: '# of Visits',
        data: myData,
        backgroundColor: 'rgba(255, 00, 46, 0.5)',
        borderColor: 'rgba(0, 0, 0, 0.3)',
        borderWidth: 1,
      }],
    },
    options: {
      responsive: true,
      fill: true,
      pointRadius: 10,
      pointHoverRadius: 100,
      maintainAspectRatio: false,
      scales: {
        yAxes: [{
          ticks: {
            beginAtZero: true,
          },
        }],
      },

    },
  });
  chart.width += 0;
};

export default {
  name: 'Graph',
  props: {
    data: Array,
  },
  mounted() {
    drawGraph();
  },
};
</script>

<style scoped>
.canvasWrap {
  height: 50vh;
}
</style>
