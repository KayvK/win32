---
Description: 'When a new thread is created by the CreateThread or CreateRemoteThread function, a handle to the thread is returned.'
ms.assetid: 'ff91fe27-9773-4185-bc1e-57e897be3821'
title: Thread Handles and Identifiers
---

# Thread Handles and Identifiers

When a new thread is created by the [**CreateThread**](createthread.md) or [**CreateRemoteThread**](createremotethread.md) function, a handle to the thread is returned. By default, this handle has full access rights, and—subject to security access checking—can be used in any of the functions that accept a thread handle. This handle can be inherited by child processes, depending on the inheritance flag specified when it is created. The handle can be duplicated by [**DuplicateHandle**](base.duplicatehandle), which enables you to create a thread handle with a subset of the access rights. The handle is valid until closed, even after the thread it represents has been terminated.

The [**CreateThread**](createthread.md) and [**CreateRemoteThread**](createremotethread.md) functions also return an identifier that uniquely identifies the thread throughout the system. A thread can use the [**GetCurrentThreadId**](getcurrentthreadid.md) function to get its own thread identifier. The identifiers are valid from the time the thread is created until the thread has been terminated. Note that no thread identifier will ever be 0.

If you have a thread identifier, you can get the thread handle by calling the [**OpenThread**](openthread.md) function. **OpenThread** enables you to specify the handle's access rights and whether it can be inherited.

A thread can use the [**GetCurrentThread**](getcurrentthread.md) function to retrieve a *pseudo handle* to its own thread object. This pseudo handle is valid only for the calling process; it cannot be inherited or duplicated for use by other processes. To get the real handle to the thread, given a pseudo handle, use the [**DuplicateHandle**](base.duplicatehandle) function.

To enumerate the threads of a process, use the [**Thread32First**](base.thread32first) and [**Thread32Next**](base.thread32next) functions.

 

 


