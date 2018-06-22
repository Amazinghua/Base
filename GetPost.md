## c#从jobject中获取相应的数据、获取数据流-防sql注入  ##

        /// <summary>
        /// 获取数据流
        /// </summary>
        /// <returns></returns>
        public string getpost()
        {
            string g = "";
            if (HttpContext.Current.Request.InputStream != null)
            {
                System.IO.StreamReader sr = new System.IO.StreamReader(HttpContext.Current.Request.InputStream, System.Text.Encoding.UTF8);
                g = sr.ReadToEnd();
            }
            return g;
        }




        /// <summary>
        /// 从jobject中获取相应的数据 
        /// </summary>
        /// <param name="jobj">jobject对象</param>
        /// <param name="key">要获取的值</param>
        /// <returns></returns>
        public string jobject(JObject jobj, string key)
        {
            string hh = "";
            if (jobj[key] != null)
            {
                hh = jobj[key].ToString().Trim();
            }
            string inj_str = "'| and | exec | insert | select | delete | update | count |*|%| chr | mid | master | truncate | char | declare |;| or |+|/";
            string inj_strA = inj_str.ToUpper();
            string[] injStra = inj_str.Split('|');
            string[] injStrA = inj_strA.Split('|');
            foreach (var inj in injStra)
            {
                hh = hh.Replace(inj, "");
            }
            foreach (var inj in injStrA)
            {
                hh = hh.Replace(inj, "");
            }
            return hh;
        }

举例


##  ##

            public void ProcessRequest(HttpContext context)
        {
            context.Response.ContentType = "text/plain";
            string result = "";
            string type = "";
            string total = "";
            int pageSize = 2;
            try
            {
                string poststr = getpost();
                if (!string.IsNullOrEmpty(poststr))
                {
                    JObject jobj = JObject.Parse(poststr);
                    type = jobject(jobj, "type");
                    string namevalue = jobject(jobj, "name");