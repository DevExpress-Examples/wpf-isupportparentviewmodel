<!-- default badges list -->
[![](https://img.shields.io/badge/Open_in_DevExpress_Support_Center-FF7200?style=flat-square&logo=DevExpress&logoColor=white)](https://supportcenter.devexpress.com/ticket/details/T1258387)
[![](https://img.shields.io/badge/📖_How_to_use_DevExpress_Examples-e9f6fc?style=flat-square)](https://docs.devexpress.com/GeneralInformation/403183)
[![](https://img.shields.io/badge/💬_Leave_Feedback-feecdd?style=flat-square)](#does-this-example-address-your-development-requirementsobjectives)
<!-- default badges end -->
# WPF MVVM Framework - Utilize the ISupportParentViewModel Interface

This example demonstrates how to utilize the `ISupportParentViewModel` interface to expose the parent view model to utilize in child view models. The interface is implemented in `ViewModelBase` descendants out of the box. This example also demosntrates how to utilize the interface in custom view models.



# Implementation details
You can use the `ViewModelExtensions.ParentViewModel` attached property to set the `ParentViewModel` in child view models.

```xaml
<local:ChildView dxmvvm:ViewModelExtensions.ParentViewModel="{Binding DataContext, ElementName=LayoutRoot}"/>
``` 

Please note that the property will be set only after the child view is fully initialized. It is not available in the view model constructor.
___
The `ISupportParentViewModel` interface enables child view models to utilize MVVM services associated with the parent. 

```cs
IMessageBoxService MessageBoxService {
    get { return GetService<IMessageBoxService>(ServiceSearchMode.PreferParents); }
}
```

__

You may need to raise `INotifyPropertyChanged` notifications for the `ParentViewModel` property. In `ViewModelBase` descendants, you can override the `OnParentViewModelChanged` method to accomplish this.

```cs
protected override void OnParentViewModelChanged(object parentViewModel) {
    RaisePropertyChanged(nameof(ISupportParentViewModel.ParentViewModel));
}
``` 

## Files to Review

- link.cs (VB: link.vb)
- link.js
- ...

## Documentation

- [ViewModel relationships (ISupportParentViewModel)](https://docs.devexpress.com/WPF/17449/mvvm-framework/viewmodels/viewmodel-relationships-isupportparentviewmodel)
- [Services](https://docs.devexpress.com/WPF/17414/mvvm-framework/services)
- [View Models](https://docs.devexpress.com/WPF/17439/mvvm-framework/viewmodels)

## More Examples

- link
- link
- link
<!-- feedback -->
## Does this example address your development requirements/objectives?

[<img src="https://www.devexpress.com/support/examples/i/yes-button.svg"/>](https://www.devexpress.com/support/examples/survey.xml?utm_source=github&utm_campaign=wpf-isupportparentviewmodel&~~~was_helpful=yes) [<img src="https://www.devexpress.com/support/examples/i/no-button.svg"/>](https://www.devexpress.com/support/examples/survey.xml?utm_source=github&utm_campaign=wpf-isupportparentviewmodel&~~~was_helpful=no)

(you will be redirected to DevExpress.com to submit your response)
<!-- feedback end -->
