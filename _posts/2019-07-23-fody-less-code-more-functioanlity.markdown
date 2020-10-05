---
layout: post
title:  "Fody: less code - more functionlity"
date:   2019-07-23 08:00:07
description: The power of Fody, summarized.
image: https://github.com/Fody/PropertyChanged/raw/master/package_icon.png
published: true
tags: fody mvvm
---

## PropertyChanged.FOdy

When using the MVVM pattern in C# I think it’s very useful to use [PropertyChanged.Fody](https://github.com/Fody/PropertyChanged){:target="_blank"}. It injects code at compile time and as a result, the code becomes cleaner and better readable.

Before code:

```csharp
public class Person : INotifyPropertyChanged
{
    public event PropertyChangedEventHandler PropertyChanged;
    
    public string GivenNames { get; set; }
    public string FamilyName { get; set; }
    public string FullName => $"{GivenNames} {FamilyName}";
}
```
What gets compiled:

```csharp
public class Person : INotifyPropertyChanged
{
    public event PropertyChangedEventHandler PropertyChanged;
    string givenNames;
    public string GivenNames
    {
        get => givenNames;
        set
        {
            if (value != givenNames)
            {
                givenNames = value;
                OnPropertyChanged(InternalEventArgsCache.GivenNames);
                OnPropertyChanged(InternalEventArgsCache.FullName);
            }
        }
    }
    string familyName;
    public string FamilyName
    {
        get => familyName;
        set 
        {
            if (value != familyName)
            {
                familyName = value;
                OnPropertyChanged(InternalEventArgsCache.FamilyName);
                OnPropertyChanged(InternalEventArgsCache.FullName);
            }
        }
    }
    public string FullName => $"{GivenNames} {FamilyName}";
    protected void OnPropertyChanged(PropertyChangedEventArgs eventArgs)
    {
        PropertyChanged?.Invoke(this, eventArgs);
    }
}
internal static class InternalEventArgsCache
{
    internal static PropertyChangedEventArgs FamilyName = new PropertyChangedEventArgs("FamilyName");
    internal static PropertyChangedEventArgs FullName = new PropertyChangedEventArgs("FullName");
    internal static PropertyChangedEventArgs GivenNames = new PropertyChangedEventArgs("GivenNames");
}
```


What a tremendous improvement!