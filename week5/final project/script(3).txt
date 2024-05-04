var Humidity = 0;
var Humidity_dataPoints = Array.from({length:60},(_,i)=>{
    var date = new Date
    date.setSeconds(date.getSeconds()-(60-i));
    return{ x: date, y:Humidity };
}
);

var Humidity_chart = new CanvasJS.Chart("Humidity_chart", {
    title: {
        text: "Humidity"
    },

    axisX: {
        interval: 1,
        intervalType: "minute",
        valueFormatString: "hh:mm"
    },

    axisY: {
        suffix:"%"
    },
    
    data: [
        {
            type: "line",
            xValueType: "dateTime",             
            dataPoints: Humidity_dataPoints
        }
    ]
});

Humidity_chart.render();
setInterval(function (   ) {
    var currentTime = new Date();
    Humidity = Math.random() * 100
    Humidity_dataPoints.push({
        x: currentTime,
        y: Humidity
    });
    if(Humidity_dataPoints.length > 60){
        Humidity_dataPoints.shift();
    }
    Humidity_chart.render();
}, 1000);

var Temperature = 0;
var Temperature_dataPoints = Array.from({length:60},(_,i)=>{
    var date = new Date
    date.setSeconds(date.getSeconds()-(60-i));
    return{ x: date, y:Temperature };
}
);

var Temperature_chart = new CanvasJS.Chart("Temperature_chart", {
    title: {
        text: "Temperature"
    },

    axisX: {
        interval: 1,
        intervalType: "minute",
        valueFormatString: "hh:mm"
    },

    axisY: {
        suffix:"°C"
    },
    
    data: [
        {
            type: "line",
            xValueType: "dateTime",             
            dataPoints: Temperature_dataPoints
        }
    ]
});

Temperature_chart.render();
setInterval(function (   ) {
    var currentTime = new Date();
    Temperature = Math.random() * 100
    Temperature_dataPoints.push({
        x: currentTime,
        y: Temperature
    });
    if(Temperature_dataPoints.length > 60){
        Temperature_dataPoints.shift();
    }
    Temperature_chart.render();
}, 1000);