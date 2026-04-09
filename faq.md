# Frequently Asked Questions

## Is This Legal / Safe to Use?

A few things worth clarifying up front -- this isn't for everyone, but it's very easy to set up if you do want to try it.

**On reverse engineering and the EULA:** Reverse engineering for interoperability is explicitly protected under the DMCA ([17 U.S.C. § 1201(f)](https://www.law.cornell.edu/uscode/text/17/1201)) and similar laws in the EU. This is the same legal basis that allows tools like Homebrew, Hammerspoon, and countless other macOS utilities that hook into Apple apps. Apple's EULA doesn't override federal law. That said, SpliceKit doesn't really involve reverse engineering in the traditional sense -- once the library is loaded, Final Cut Pro exposes all of its own classes and methods through the Objective-C runtime. There's no decompilation required.

**On "injecting code":** What SpliceKit does is no different from what accessibility tools, screen readers, and automation utilities do every day on macOS. `DYLD_INSERT_LIBRARIES` is a documented Apple mechanism -- it's not an exploit. Apps like BetterTouchTool, Alfred, and Bartender all inject into running processes using the same techniques.

**On Apple disabling your Apple ID:** There is no precedent for Apple disabling an Apple ID for running a modified local app. Apple can't even distinguish between "ran a modded app" and "loaded a dylib for debugging in Xcode," which developers do constantly. Apple's focus is on protecting the App Store and code signing for distribution -- not policing what developers do on their own machines.

**The real risk** is the same as any unsigned software: make sure you trust the source. The code is fully open, the techniques are well-established, and nothing here is novel or dangerous from a security perspective.

On a personal note -- I've been frustrated by how little progress Final Cut Pro has made over the years, and my hope is that this project can help it finally get some of the features it desperately needs. There's a huge precedent in modding software and games. I've modded quite a few games where the developers officially adopted features based on community work. It can be a really productive relationship where proof of concepts demonstrate what would be genuinely useful to add officially.
