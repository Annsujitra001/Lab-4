# Lab-4

2. สร้างและรัน Spatial Model

        ขั้นตอนการวิเคราะห์ (Spatial MCA Model)
           1. การ Normalize ข้อมูล
              แต่ละปัจจัยมีหน่วยต่างกัน (mm, meter, degree) จึงต้องทำให้เป็นมาตรฐานเดียวกันก่อน
                	ใช้วิธี Min-Max Normalization
              เหตุผล:
	  				> ทำให้ค่าทุก layer อยู่ในช่วง 0–1 
	  				> สามารถนำมารวมกันแบบ weighted sum ได้
   		   2. การรวมปัจจัย (Weighted Overlay Model)
			   โมเดลความเสี่ยงน้ำท่วม  เป็น Linear Combination Model ที่นิยมใน GIS-based risk assessment
		   3. การแบ่งระดับความเสี่ยง (Classification)
			   ใช้ threshold แบบ rule-based:
   					> Low Risk: < 0.4
   					> Moderate Risk: 0.4 – 0.7
   					> High Risk: > 0.7 
			  เหตุผลของ threshold:
   					> ใช้การแบ่งเชิง heuristic (Quantile-like interpretation)
   					> แยกกลุ่มความเสี่ยงเพื่อให้ map อ่านง่าย 
					> ใช้สำหรับการสื่อสารเชิงนโยบาย (policy-friendly classification)
   			  ผลลัพธ์ (Output Map)
					ผลลัพธ์สุดท้ายเป็นแผนที่:
						> 🟢 Low risk
   						> 🟡 Moderate risk
   						> 🔴 High risk 
					แสดงเฉพาะพื้นที่ จังหวัดนครศรีธรรมราช โดยใช้การ clip จาก GAUL boundary

3. Sensitivity Analysis

		3.1 ลองเปลี่ยนน้ำหนักของปัจจัยที่สำคัญที่สุด ±20% แล้วดูว่าผลลัพธ์เปลี่ยนอย่างไร
				กรณีที่ 1: เพิ่มน้ำหนักฝน +20% 
							W_rain_high=0.4×1.2  แล้ว normalize ใหม่ให้ผลรวมยังเท่ากับ 1 
	  			เพื่อ จำลองสถานการณ์ที่ “ฝนมีอิทธิพลมากขึ้นผิดปกติ”
   				กรณีที่ 2: ลดน้ำหนักฝน -20%
							W_rain_low=0.4×0.8
				เพื่อจำลองกรณีที่ rainfall influence ลดลง
				ความหมายของผลลัพธ์
					•	ค่า > 0 → ความเสี่ยงเพิ่มขึ้นเมื่อเพิ่มน้ำหนักฝน 
					•	ค่า < 0 → ความเสี่ยงลดลงเมื่อเพิ่มน้ำหนักฝน 
					•	ค่า ≈ 0 → โมเดลไม่ไวต่อการเปลี่ยนแปลง (robust area)
		3.2 ข้อสรุปของ Sensitivity Analysis มีผลต่อความเชื่อมั่นในโมเดลอย่างไร?
				ความน่าเชื่อถือเพิ่มขึ้น เพราะ:
   					> โมเดลไม่เปลี่ยนแบบสุ่ม
   					> พฤติกรรมสอดคล้องกับหลักอุทกวิทยา
   					> สามารถอธิบายพื้นที่ที่ sensitive vs robust ได้






































































