<!DOCTYPE html>
<html lang="ja">
<head>
	<meta charset="UTF-8">
	<title>Chart.js+Vue.js+Axios</title>
	<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0/dist/Chart.min.js"></script>
</head>
<body>
  <div style="width:600px">
    <canvas id="myChart"></canvas>
  </div>
<script>
  var ctx = document.getElementById('myChart').getContext('2d');
  var myChart = new Chart(ctx, {
      type: 'line',
      data: {
          labels: ['2019年1月', '2019年2月', '2019年3月', '2019年4月'],
          datasets: [{
              label: '四半期の売上数の遷移',
              data: [120, 190, 34, 58]
            }
          ]
      }
  });
</script>
</body>
</html>
