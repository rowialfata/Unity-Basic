# Tutorial and Script Dedicated for Newbie Develepor
All content in this repo is free. Everyone is allowed to use, copy, modify, merge, publish, distribute, sublicense, and/or sell it with and/or without any permission.

### Camera to follow player
```
    public Transform player;
    public Vector3 offset;

    // Update is called once per frame
    void Update()
    {
        transform.position = player.position + offset;
    }
```

### Count the score based on distance
```
    public Transform player;
    public Text scoreText;

    private void Start()
    {
        scoreText = GetComponent<Text>();
    }

    void Update()
    {
        scoreText.text = player.position.z.ToString("0");
    }
```

### Car Engine
```
        mobil.AddForce(kecepatan * Time.deltaTime, 0, 0);

        if(Input.GetKey("d"))
        {
            Debug.Log("belok kiri");
            mobil.AddForce(0, 0 , -belok * Time.deltaTime, ForceMode.VelocityChange);
        }

        if (Input.GetKey("a"))
        {
            Debug.Log("belok kiri");
            mobil.AddForce(0, 0, belok * Time.deltaTime, ForceMode.VelocityChange);
        }
```

### Game End
```
    public void EndGame()
    {
        if(gameHasEnded == false)
        {
            nabrakAudio.Play();
            gameHasEnded = true;
            textTamat.SetActive(true);
            tombolUlang.SetActive(true);
            suaraMobil.enabled = false;

            carScript.enabled = false;
        }
    }
```

### Count down
```
private void Start()
    {
        //define the gameobject
        mobil = GameObject.Find("car scene").gameObject;

        //get the script from the gameobject
        mesinMobil = mobil.GetComponent<CarEngine>();
    }

    void Update()
    {
        if( time > 1 )
        {
            time -= Time.deltaTime;
            count.text = time.ToString("0");
        }

        else
        {
            count.enabled = false;
            //activate the script of car engine
            mesinMobil.enabled = true;
        }
    }
```

### Collision
```
    private void OnCollisionEnter(Collision collision)
    {
        if (collision.collider.tag == "Halangan2")
        {
            halangan2.Play();
            ledakanKecil.Play();
        }

        if (collision.collider.tag == "Halangan")
        {
            ledakan.Play();
            movement.enabled = false;
            //FindObjectOfType<GameManager>().EndGame();
        }
    }
```

### Open another apps
```
 bool fail = false;
            string bundleId = com.google.appname; // your target bundle id
            AndroidJavaClass up = new AndroidJavaClass("com.unity3d.player.UnityPlayer");
            AndroidJavaObject ca = up.GetStatic<AndroidJavaObject>("currentActivity");
            AndroidJavaObject packageManager = ca.Call<AndroidJavaObject>("getPackageManager");
     
            AndroidJavaObject launchIntent = null;
            try
            {
                launchIntent = packageManager.Call<AndroidJavaObject>("getLaunchIntentForPackage",bundleId);
            }
            catch (System.Exception e)
            {
                fail = true;
            }
 
            if (fail)
            { //open app in store
                Application.OpenURL("https://google.com");
            }
            else //open the app
                ca.Call("startActivity",launchIntent);
 
            up.Dispose();
            ca.Dispose();
            packageManager.Dispose();
            launchIntent.Dispose();
```
