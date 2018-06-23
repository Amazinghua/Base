## js用户输入正则验证 ##

     //“^”是代表以什么开头，“$”是代表以什么结尾。比如：/^\dA$/ //这个就匹配，以数字开头，并且一大写字母A结尾的字符串。
            //var reg_username = /[A-Za-z][A-Za-z0-9_]{6,16}/;
            var reg_username = /^[a-zA-Z][a-zA-Z0-9]{5,16}$/;
            var reg_password = /^[a-zA-Z0-9_]{6,12}$/;
            var reg_mail = /^\w+@\w+(\.[a-zA-Z]{2,3}){1,2}$/;
            var reg_phone = /^1\d{10}$/;
            var reg_birthday = /^([12]\d{3})-(([1-9])|(1[012])|(0[1-9]))-(([1-9])|([12]\d)|(3[01]))$/;
            //身份证校验： reg=/\d{17}[0-9xX]/ 前17位为数字第18位为数字或者字母X或x          

            if (!reg_username.test(username)) //用户名判断
            {
                alert("用户名输入有误，只能是字母数字下划线，6-16位");
            }
            else if (!reg_password.test(password)) {
                alert("密码输入有误，只能是字母数字下划线6-12位");
            }
            else if (confirm != password) {
                alert("两次密码输入的不一致");
            }
            else if (!reg_mail.test(email)) {
                alert("邮箱输入有误")
            }
            else if (!reg_phone.test(phone)) {
                alert("手机号输入有误");
            }
            else if (!reg_birthday.test(birthday)) {
                alert("日期输入不正确");
            }
            else if (!checkGender()) {
                alert("请选择性别");
            } else if (!checkHobbys()) {
                alert("请至少选择一项兴趣");
            }