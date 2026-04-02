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





































































