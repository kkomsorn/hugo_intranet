# Intranet  

เป็นระบบที่รวบรวมการเข้าถึงเว็บไซต์ภายในต่างๆของ Egati  
ออกแบบและพัฒนาโดย สทอ.  
- พัฒนาโดย Hugo v0.79.1/extended windows/amd64
- HTML สำหรับการแก้ไขหน้า UI  
- ใช้ Theam Hugo Airspace

## ตัวอย่างหน้า Intranet  
![image](/static/img/EXAMPLE.png)  
   
## คำที่จะใช้
- **Custom** ปรับปรุงแก้ไข หน้าตา สี รูปแบบ
- **แก้ไข** ปรับปรุงการทำงานของโค้ด
  
## ส่วนประกอบที่สำคัญของ Intranet  
- **header** โค้ดส่วนที่เกี่ยวข้องมีดังนี้  
    - config.toml ในที่นี้มีหน้าที่ใส่ลิงค์ให้กับหัวข้อบน Navbar  
    ```toml   
    [[menu.header2]]
      weight = 1
      name = "เบอร์โทรติดต่อภายใน"
      url = "https://easy.egati.co.th/egaticontact/"
    [[menu.header2]]
      weight = 2
      name = "ข่าวสารและประชาสัมพันธ์"
      url = "https://info.egati.co.th/processwire_news/my_blog/"

      # ถ้าต้องการเพิ่มแถบบน Navbar ให้ Copy [[menu.header2]] ทั้งหัวข้อแล้วางและแก้ไขชื่อและ Url ได้เลย
    ```
    - header.html มีหน้าที่กำหนด Format ต่างๆให้กับ navbar
    ```html
    - Custom Navbar <nav class="navbar navbar-fixed-top navbar-dark" style="background-color: #32446b ; margin-bottom: 0px;"> 
    - Custom Logo <img src="{{ .Site.BaseURL }}img/biglogo.png" style="height: 50px; width: 50px; float: left; margin-top: 13px;margin-right: 10px;">
    - Custom คำข้าง Logo <a href="{{ .Site.BaseURL }}"><h2 class="h2-nav text-primary" style="color:#F7D923 ; font-family: 'Prompt', sans-serif; margin-top: 20px; display: inline-block;" >EGATi</h2></a> 
    - Custom คำทางด้านขวา <li ><a href="{{ .URL }}" class=" magnifyBtn" target="_blank"><p class="p-nav" style="color: #F7D923;"> {{ .Name }}</p></a></li>
    ```  
- **Body** โค้ดที่สำคัญมีดังนี้  
    - alllink.html เป็นส่วนที่แสดงลิ้งค์ทั้งหมดในรูปแบบ Logo 
    ```html
    alllink ในโค้ด หมายถึง ไฟล์ allling.yml
    {{ range .Site.Data.alllink.items }}
        <div class="col-md-5th-1 col-sm-4 card-1" style="padding-left: 0px;">
          <div align="center" class="magnifyBtn" onclick="window.open({{ .url }} ,'_blank')">
            <div style="height: 30px;"></div>
            <div class="card-body cursorPointer">
    Custom รูป(โลโก้)         <p class="card-text-icon"><a href="{{ .url }}" target="_blank" class="iconLink text-primary"
                  style="color: #F7D923 ;"><i class="fa-5x {{ .icon }}"
                    style="stroke: #878683; stroke-width: 0px; font-size: 6em;"></i></a></p>
    ข้อความ(ชื่อลิงค์)          <p class="card-text"><a href="{{ .url }}" target="_blank" class="iconLink text-primary"
                  style="color: #32446b; font-family:Prompt ; font-size: 24px;">{{ .title | safeHTML }}</a></p>
            </div>
          </div>
        </div>
    {{ end }}
    ```
    - alllink.yml เป็นไฟล์ที่กำหนดชื่อ ไอคอน และลิ้งค์ของ สิ่งที่แสดงในส่วน Body 
    ```yml
    #EXAMPLE

    enable: true # กำหนดไว้เสมอว่าเป็น True 
    group: ระบบงานสารสนเทศ # ชื่อกลุ่ม ชื่อหัวข้อหลักที่จะแสดง
    items:

  - title: จองห้องประชุม # ชื่อลิงค์ ชื่อที่จะใช้ในการแสดงผล
    url: http://10.20.8.114/sites/intranet/02/SitePages/Home.aspx # Url ที่เราต้องการ
    icon: fas fa-door-open # ไอคอน รูปไอคอนที่เราจะใช้

    # เมื่อต้องการเพิ่มหัวข้อใหม่ให้ Copy ไปตั้งแต่ title จนถึง icon และนำไปแก้ไขแต่ละหัวข้อตามที่ต้องการ
    ```
- **footer** โค้ดที่สำคัญมีดังนี้
    - footer.html ไฟล์ที่กำหนดข้อความ สี และอื่นของ footer 
    ```html
    <nav class="navbar navbar-fixed-bottom navbar-dark" style="background-color:  #32446b;"> <!--Custom สีของ footer-->
    <h2 class="h2-nav text-primary" style="color:#F7D923 ; font-family: 'Kanit', sans-serif; margin-top: 20px; display: inline-block; font-size: 20px;" >บริษัท กฟผ.อินเตอร์เนชั่นแนล จำกัด</h2> <!--Custom สี ขนาด ฟอนต์ ของ ข้อความ "บริษัท กฟผ.อินเตอร์เนชั่นแนล จำกัด"-->
    <h2 class="h2-nav text-primary" style="color:#F7D923 ; font-family: 'Kanit', sans-serif; margin-top: 20px; display: inline-block; font-size: 20px;" >จัดทำโดย &ensp;สทอ. &emsp; ติดต่อ โทร 66938</h2> <!--Custom สี ขนาด ฟอนต์ ของ ข้อความ "จัดทำโดย สทอ. ติดต่อ โทร 66938"-->

    ```
- **CSS** ใช้ไฟล์ Style.css  
  


## การเพิ่มลิงค์ใหม่  

- ไปที่ไฟล์ alllink.yml
- Copy

    ```yml
    - title: จองห้องประชุม 
      url: http://10.20.8.114/sites/intranet/02/SitePages/Home.aspx
      icon: fas fa-door-open
    ```
- วางไว้ที่ล่างสุด หรือ ตำแหน่งที่ต้องการ
- แก้ไขหัวข้อที่ต้องการ
- Save File

## การเพิ่มหัวข้อบน Navbar
- ไปที่ไฟล์ config.toml
- Copy

    ```toml
      [[menu.header2]]
      weight = 2 # กำหนดลำดับก่อนหลังให้ข้อความ
      name = "ข่าวสารและประชาสัมพันธ์" # ข้อความที่จะแสดง
      url = "https://info.egati.co.th/processwire_news/my_blog/" # Url ที่จะเชื่อมไป

    ```
- วางไว้ในหัวข้อ [[menu]]
- แก้ไขหัวข้อที่ต้องการ
- Save File