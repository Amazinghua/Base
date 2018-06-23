## layui实现分页 ##
引入

    <script src="layui/layui.all.js"></script>
    <script src="layui/lay/modules/laypage.js"></script>
    <link href="layui/css/layui.css" rel="stylesheet" />

回调函数

            function list(data) {
            var tb = window.document.getElementById("tbody-result");
            var str = "";
            if (data.result == "888") {
                var data = data.table;
                //调用分页
                layui.use(['laypage', 'layer'], function () {
                    var laypage = layui.laypage
                        , layer = layui.layer;
                    //调用分页
                    laypage.render({
                        elem: 'page'
                        , count: data.length
                        , limit:2
                        , jump: function (obj) {
                            //模拟渲染
                           
                            tb.innerHTML = function () {
                                var arr = []
                                    , thisData = data.concat().splice(obj.curr * obj.limit - obj.limit, obj.limit);
                                
                                layui.each(thisData, function (i, data) {
                                    arr.push("<tr>" +
                                        "<td>" + thisData[i].id + "</td>" +
                                        "<td>" + thisData[i].stuNo + "</td>" +
                                        "<td>" + thisData[i].courseName + "</td>" +
                                        "<td>" + thisData[i].courseScore + "</td>" +
                                        "</tr>");
                                });
                                return arr.join('');
                                console.log(arr);
                                tb.appendChild(arr);
                            }();
                        }
                    });
                });

            }
        }