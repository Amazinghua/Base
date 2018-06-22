## c#实现模糊查询-sql语句 ##
            public static string ArrayKeyWord(string keywords, string dbstruture)
        {
            string condition = "";
            string[] keywordList = dbstruture.Split('|');
            try
            {
                if(keywordList.Length > 1)
                {
                    for(int i = 0; i < keywordList.Length; i++)
                    {
                        condition += keywordList[i] + " like '%" + keywords + "%' or ";

                    }
                    condition = condition.Substring(0, condition.Length - 3);
                    condition = condition.Replace("[", "[[]");
                }
            } catch(Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
            return condition;
        }