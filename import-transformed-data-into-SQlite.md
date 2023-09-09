* # wiki

import pandas as pd
import sqlite3
Wiki = pd.read_excel(r"C:\Users\IT_ADMIN.DESKTOP-PL4LGAS\Documents\DA_Hibreed\flatten_data_table-main\wikipedia_dataset_flatX1.xlsx")

db_conn = sqlite3.connect(r"C:\Users\IT_ADMIN.DESKTOP-PL4LGAS\Documents\DA_Hibreed\flatten_data_table-main\wikipedia.db")

c = db_conn.cursor()


Wiki.to_sql('wiki', db_conn, if_exists='append', index=False)