Help me generate an agent that connects to postgres and can query data  import psycopg2  def read_postgres_database(db_name, db_user, db_password, db_host, db_port, table_name): conn = None  # Initialize conn to None  try: conn = psycopg2.connect(dbname=db_name, user=db_user, password=db_password, host=db_host, port=db_port) cursor = conn.cursor() cursor.execute(f"SELECT * FROM {table_name}") rows = cursor.fetchall() return rows  except psycopg2.Error as e: print(f"Database error: {e}") return [] finally: if conn: conn.close()





-------
Help me generate an agent that read csv use pandas  import pandas as pd  df = pd.read_csv('data.csv') print(df.to_string())




----

This API generates random user data,useful for testing and development import requests response = requests.get('https://randomuser.me/api/') if response.status_code == 200: data = response.json() user = data['results'][0] print(f"Name: {user['name']['first']} {user['name']['last']}") print(f"Email: {user['email']}") print(f"Address: {user['location']['street']['name']}, {user['location']['city']}, {user['location']['state']}") else: print(f"Request failed with status code: {response.status_code}")


------ 经纬度天气
Help me generate an agent,Given a longitude and latitude, get the temperature import requests   API doc in this url : https://open-meteo.com/ url = "https://api.open-meteo.com/v1/forecast" params = {"latitude": 52.52,  # 柏林纬度"longitude": 13.41, # 柏林经度 "hourly": "temperature_2m"}response = requests.get(url, params=params) if response.status_code == 200: data = response.json() print(f"柏林当前温度: {data['hourly'['temperature_2m'][0]}°C") else: print("请求失败")


---- 国际空间站地址
I want to create an agent to get the current latitude and longitude of the International Space Station . this code is : def track_iss(): response = requests.get("http://api.open-notify.org/iss-now.json") if response.status_code == 200: position = response.json()["iss_position"] return f"经度: {position['longitude']}, 纬度: {position['latitude']}" return "追踪失败" print(f"国际空间站实时位置：{track_iss()}")

---- 获取随机励志名言
I want to create an agent that randomly gets a list of famous quotes this code is : import requests def get_inspirational_quote(): response = requests.get("https://zenquotes.io/api/random") if response.status_code == 200: data = response.json()[0] return f"{data['q']} ——{data['a']}" return "名言获取失败" print(get_inspirational_quote())

---- 检查某日期是否为公共假日（全球范围） 
I want to create an agent that checks if a date is a global public holiday def is_public_holiday(date_str, country_code="CN"): year = date_str.split("-")[0] response = requests.get(f"https://date.nager.at/api/v3/PublicHolidays/{year}/{country_code}") if response.ok: holidays = [holiday["date"] for holiday in response.json()] return date_str in holidays  return False  print(is_public_holiday("2025-01-01"))

---- 维基百科摘要（Knowledge 分类）
I want to create an agent to query the summary information corresponding to a certain wiki . def wiki_summary(topic): response = requests.get(f"https://en.wikipedia.org/api/rest_v1/page/summary/{topic}") if response.ok: return response.json() return "未找到相关信息" print(wiki_summary("Python"))

---- 查询英文单词释义
I want to create an agent to query the meaning of a certain word def define_word(word): response = requests.get(f"https://api.dictionaryapi.dev/api/v2/entries/en/{word}") if response.ok: definition = response.json()[0]["meanings"][0]["definitions"][0]["definition"] return f"{word}: {definition}" return "未找到释义" print(define_word("serendipity"))

---- 时区转换工具
I want to create an agent, a time zone conversion tool . def get_time_in(area="Asia/Shanghai"): response = requests.get(f"http://worldtimeapi.org/api/timezone/{area}") if response.ok: return response.json()["datetime"].split("T")[1][:5] return "时间获取失败" print(f"上海当前时间: {get_time_in()}")

---- 颜色转换工具
I want to create an agent, a color conversion tool . def color_name(hex_code): response = requests.get(f"https://www.thecolorapi.com/id?hex={hex_code.lstrip('#')}") if response.ok: return response.json()["name"]["value"] return "未知颜色" print(color_name("#FF5733"))

---- 全球大学搜索（Education 分类）
I want to create an agent to get the top three universities in a country. def find_universities(country="China"): response = requests.get(f"http://universities.hipolabs.com/search?country={country}") if response.ok: return [uni["name"] for uni in response.json()[:3]]  # 返回前3所大学  return [] print(find_universities())

---- 国家信息查询(Reference 分类)
I want to create an agent to get some basic information about certain countries . country_data = requests.get("https://restcountries.com/v3.1/name/france").json()[0] print(f"首都: {country_data['capital'][0]}, 货币: {list(country_data['currencies'].keys())[0]}")

---- 加密货币实时价格（Finance 分类）  
I want to create an agent to get the real-time price of cryptocurrency . btc_price = requests.get("https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=usd").json() print(f"BTC价格: ${btc_price['bitcoin']['usd']}") # 输出示例: BTC价格: $43000



--- 
I want to create an agent .  that code is from openai import OpenAI  client = OpenAI(api_key="<DeepSeek API Key>", base_url="https://api.deepseek.com") response = client.chat.completions.create(model="deepseek-chat", messages=[{"role": "system", "content": "You are a helpful assistant"}, {"role": "user", "content": "Hello"},], stream=False) print(response.choices[0].message.content)
†


接口信息 调用地址：https://hdl.market.alicloudapi.com/diabetes/getReport 请求方式：  POST  返回类型：  JSON  API 调用： API 简单身份认证调用方法（APPCODE） API 签名认证调用方法（AppKey & AppSecret）  获取认证： AppKey & AppCode  接口参数 请求参数（Header） 无参数 请求参数（Query） 字段名称 必填 字段详情 age string N 年龄 sex string N 性别 type string N 固定参数 实例值： diabetesRisk weight string N 体重（kg） height string N 身高（米） systolicPressure string N 收缩压 diastolicPressure string N 舒张压 familyHistoryOfDiabetes string N 糖尿病家族史 实例值： 否,旁系亲属（爷爷/姥爷、奶奶/姥姥、姑、姨、叔、伯、舅、表/堂兄妹）,直系亲属（父母、兄妹、子女） historyOfHyperglycemia string N 血糖升高史（是、否） intakeOfVegetablesAndFruits string N 蔬菜、水果摄入情况（每天、偶尔） waist string N 腰围(cm)dailyExerciseTime string N 每天锻炼时间(分钟)



import urllib, urllib3, sys, uuid  import ssl  host = 'https://hdl.market.alicloudapi.com' path = '/diabetes/getReport'  method = 'POST' appcode = '你自己的AppCode' querys = 'age=18&sex=%E7%94%B7&type=diabetesRisk&weight=70&height=1.85&systolicPressure=130&diastolicPressure=100&familyHistoryOfDiabetes=%E5%90%A6%2C%E6%97%81%E7%B3%BB%E4%BA%B2%E5%B1%9E%EF%BC%88%E7%88%B7%E7%88%B7%2F%E5%A7%A5%E7%88%B7%E3%80%81%E5%A5%B6%E5%A5%B6%2F%E5%A7%A5%E5%A7%A5%E3%80%81%E5%A7%91%E3%80%81%E5%A7%A8%E3%80%81%E5%8F%94%E3%80%81%E4%BC%AF%E3%80%81%E8%88%85%E3%80%81%E8%A1%A8%2F%E5%A0%82%E5%85%84%E5%A6%B9%EF%BC%89%2C%E7%9B%B4%E7%B3%BB%E4%BA%B2%E5%B1%9E%EF%BC%88%E7%88%B6%E6%AF%8D%E3%80%81%E5%85%84%E5%A6%B9%E3%80%81%E5%AD%90%E5%A5%B3%EF%BC%89&historyOfHyperglycemia=%E5%90%A6&intakeOfVegetablesAndFruits=%E6%AF%8F%E5%A4%A9&waist=40&dailyExerciseTime=10' bodys = {} url = host + path + '?' + querys http = urllib3.PoolManager()headers = { 'X-Ca-Nonce': str(uuid.uuid4()), # 需要给X-Ca-Nonce的值生成随机字符串，每次请求不能相同 'Content-Type': 'application/json; charset=UTF-8', 'Authorization': 'APPCODE ' + appcode } bodys[''] = "{\"age\":\"18\",\"sex\":\"男\",\"weight\":\"70\",\"height\":\"1.85\",\"BMI\":\"25\",\"type\":\"diabetesRisk\",\"historyOfHyperglycemia\":\"否\",\"intakeOfVegetablesAndFruits\":\"每天\",\"waist\":\"40\",\"dailyExerciseTime\":\"10\",\"systolicPressure\":\"130\",\"diastolicPressure\":\"100\",\"familyHistoryOfDiabetes\":\"否\"}"post_data = bodys['']response = http.request('POST', url, body=post_data, headers=headers)content = response.data.decode('utf-8')if (content):print(content) 

