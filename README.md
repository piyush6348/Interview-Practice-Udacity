# Interview Practice Udacity

#### 1)  What’s your favorite tool or library for Android? Why is it so useful?
> My favourite library is Schematic. It helps to generate Content Providers for our database which helps us to access our database from widget and other applications. Another one is Rx Java- It's a new library that helps us to do network calls without using async task and we can easily switch between UI and Background thread.

#### 2) You want to open a map app from an app that you’re building. The address, city, state, and ZIP code are provided by the user. What steps are involved in sending that data to a map app?

1. First I will build a uri to pass it to the maps app.<br>
  String uri =  geo:0,0?q=my+street+address;
2. Then use the uri to create a Intent and Launch the maps activity
```java
  Intent intent = new Intent(android.content.Intent.ACTION_VIEW, Uri.parse(uri));
  intent.setClassName("com.google.android.apps.maps", "com.google.android.maps.MapsActivity");
  startActivity(intent);
  ```

#### 3) Implement a method to perform basic string compression using the counts of repeated characters. For example, the string aabcccccaaa would become a2b1c5a3. If the "compressed" string would not become smaller than the original string, your method should return the original string. The method signature is: “public static String compress(String input)” You must write all code in proper Java, and please include import statements for any libraries you use.

```java
class TestClass {
    public static String compress(String input)
    {
        StringBuffer buff=new StringBuffer("");
        
        for(int i=0;i<input.length();)
        {
            int ct=1;
            for(int j=i+1;j<input.length();j++)
            {
                if(input.charAt(i)==input.charAt(j))
                    ct+=1;
                else
                    break;
            }
            buff.append(input.charAt(i));
            buff.append(ct);
            i+=ct;
        }
        
        if(buff.length()>input.length())
            return input;
        else
            return buff.toString();
    }
    public static void main(String args[] ) throws Exception {
    
        TestClass obj=new TestClass();
        System.out.println(obj.compress("aabcccccaaa"));
        System.out.println(obj.compress("abcd"));

    }
}

```

#### 4) List and explain the differences between four different options you have for saving data while making an Android app. Pick one, and explain (without code) how you would implement it.
> Options to store data: 1. Shared preferences 2. SQLite database 3. Internal Storage 4. External storage 5. Network Connection<br>
	Shared Preferences is a key-value pair storage. It is generally used to store small amount of data.<br>
	
> To write values:
    1. Call edit() to get a SharedPreferences.Editor.<br>
    2. Add values with methods such as putInt() and putString().<br>
    3. Commit the new values with commit().<br>
    4. Use getSharedPreference method to get it.<br>
    5. Use getString(), getBoolean() methods to fetch values from it.<br>
  But this method is not so effective for large datasets.<br>
  

#### 5) What are your thoughts about Fragments? Do you like or hate them? Why?
> Fragments are parts of Activity that help in adding multiple and reusable views to an activity.
The main reason to use Fragments are for the backstack and lifecycle features. It makes it easy to reuse our views as they keep track of history of views and their states. I am in favour of using Fragments as they provide various advantages and helps in making great UI/UX.
For eg, in the case of tablets, we can use a single activity and attach two fragments to it. I have done this in one of my Nanodegree projects named Popular Movies, one for showing the list and the other for the detail. This helps us in effective utilisation of extra space on large screen devices

#### 6) If you were to start your Android position today, what would be your goals a year from now? 
> By next year, I want to see myself working with a team of android developers learning more and more technologies<br>
and implementing them to make something that would be useful for everyone.<br>
I also have plans to contibute more towards open source community.
