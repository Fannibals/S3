###Work of fixing bugs

-----

#### 10/3/2019

+ Bug- no.1
  + About: Photo
  + Desc: 添加新的图片略缩图很慢，而且会出现显示bug (如activities里的头像没有更新)
  + i_user.photo

+ Related files:

  + ProfilePhotoViewController.swift

    + UpdatePhoto

      + **the image picked is: <UIImage: 0x6000003079c0> size {1239, 930} orientation 0 scale 1.000000**

      + Info:

      + ```json
        "UIImagePickerControllerCropRect": NSRect: {{132, 512}, {1407, 1408}}, 
        
        "UIImagePickerControllerEditedImage": <UIImage: 0x600001f8d5e0> size {1242, 1242} orientation 0 scale 1.000000, 
        
        "UIImagePickerControllerImageURL":file:///Users/Ethan/Library/Developer/CoreSimulator/Devices/417A80F4-E490-4428-BA21-946470161CC6/data/Containers/Data/Application/996921CD-697B-42F7-B176-A116D266F110/tmp/C1276C55-68AB-4AE2-AF68-EA58E9066E5E.jpeg, 
        
        "UIImagePickerControllerPHAsset": <PHAsset: 0x7fbcd0caf890> 99D53A1F-FEEF-40E1-8BB3-7DD55A43C8B7/L0/001 mediaType=1/0, sourceType=1, (1668x2500), creationDate=2012-08-08 21:29:49 +0000, location=1, hidden=0, favorite=0 , 
        
        "UIImagePickerControllerReferenceURL": assets-library://asset/asset.JPG?id=99D53A1F-FEEF-40E1-8BB3-7DD55A43C8B7&ext=JPG, "UIImagePickerControllerMediaType": public.image
        ```

      + AVFile - LeanCloud

      + didset and wiliest

+ Reason:
  + Didn't reload the tableview's data after changing the avatar
  + Photos are wrongly chosed
+ Status: the speed problem is still exist



#### 11/3/2019

+ Bug 2: 
  + Desc: 
    + meetings页面事件卡片左划后，点击任意按钮（置顶、静音、归档）必定闪退。
  + Related files
    + EventUtility.swift

+ call back的东西不对

  + response is weird

  + ​    **data =     {**

    ​        **"__server__placeholder" = placeholder;**

    ​    **};**

    ​    **info = failed;**

    ​    **status = "-1";**

    ​    **syncToken = "";**

  + let models:[ITimeEvent] = Mapper<ITimeEvent>().mapArray(JSONObject: json["data"])!

+ Api:?
  + "http://dev.timagic.net/api/event/mute/3/D3B598C6-EB04-415A-8944-B4F12F9589AD/0?syncToken=2019-03-13+11%253A44%253A01"	

