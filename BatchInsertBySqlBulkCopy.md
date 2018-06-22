## c#批量插入数据库-excel内存表 ##
    
        /// <summary>
        /// 批量插入SqlBulkCopy
        /// </summary>
        /// <param name="dt"></param>
        /// <param name="tableName">表名</param>
        public static void BatchInsertBySqlBulkCopy(DataTable dt, string tableName)
        {
            using (SqlBulkCopy sbc = new SqlBulkCopy(System.Configuration.ConfigurationManager.ConnectionStrings["ConnectionString"].ToString()))
            {
                sbc.BatchSize = dt.Rows.Count;
                sbc.BulkCopyTimeout = 10;
                sbc.DestinationTableName = tableName;
                for (int i = 0; i < dt.Columns.Count; i++)
                {
                    sbc.ColumnMappings.Add(dt.Columns[i].ColumnName, i);
                }
                //全部写入数据库
                sbc.WriteToServer(dt);
            }
        }