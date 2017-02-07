#UIImage与字符串互转

##将image转为字符串
NSData *data = UIImageJPEGRepresentation(editedImg, 1.f);
NSString *imgStr = [data base64EncodedStringWithOptions:NSDataBase64Encoding64CharacterLineLength];
##将字符串转为image
NSData *data = [[NSData alloc] initWithBase64EncodedString:imgStr options:NSDataBase64DecodingIgnoreUnknownCharacters];
UIImage *image = [UIImage imageWithData:data];