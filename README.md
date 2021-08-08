# Text-to-speech
1)Install packeg

ibm_watson

ibm_cloud_sdk_core

<img width="1043" alt="Screen Shot 1442-12-29 at 6 22 20 AM" src="https://user-images.githubusercontent.com/56722657/128619670-f1703de2-4fa2-4839-9e9e-404d53f577c2.png">
<img width="1048" alt="Screen Shot 1442-12-29 at 6 21 48 AM" src="https://user-images.githubusercontent.com/56722657/128619672-27663615-fda8-453c-9830-635b6f5b8693.png">

Authenticate...

from ibm_watson import TextToSpeechV1

from ibm_cloud_sdk_core.authenticators import IAMAuthenticator

api = IAMAuthenticator("yu0nbGg2MftCM2pwJ-vfPIU3av-hohceTq4xd2GWKK0V")

t2s=TextToSpeechV1(authenticator=api)

t2s.set_service_url("https://api.us-east.text-to-speech.watson.cloud.ibm.com/instances/f8d41c04-d1f9-41eb-96e1-3bd40261f1a4")


Reading from a File...



with open('/Users/abeerabdullah/TextToSpeech/churchill.txt', 'r') as f:

    text = f.readlines()
    
    text = [line.replace('\n', '') for line in text]
    
text = ''.join(str(line) for line in text)

with open('./winston.mp3', 'wb') as audio_file:

    res = t2s.synthesize(text, accept='audio/mp3', voice='en-GB_JamesV3Voice').get_result()
    
    audio_file.write(res.content)


<img width="1403" alt="Screen Shot 1442-12-29 at 6 03 42 AM" src="https://user-images.githubusercontent.com/56722657/128619945-79554768-cc76-4d81-b150-89ad7131525d.png">


