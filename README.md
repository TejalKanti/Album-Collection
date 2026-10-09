# Album Collection App

**Developer**: Tejal Kanti 

**Student Number**: ST10513267

**Group**: 2

**Course**: MAST

**Subject**: Mobile App Scripting

---


## Links: 

**GitHub Repository**: https://github.com/TejalKanti/Album-Collection.git

---

## Project Overview

The Album Collection App is a website application developed as part of an ICE Task in the MAST subject. This application was created using react native. 

---

## Development Environments

1. **Expo**
   
2. **React Native**
   
3. **TypeScript**
   
4. **Institutional VM**
   
5. **Blue Stacks 5**

6. **Expo Go**

---

## ### Error Log Table

| # | Location | Problem | Error Type | Correction |
| :-: | :--- | :--- | :--- | :--- |
| **1** | `App.tsx`<br>(Line 62) | **Impossible Character Length Validation (Title)**<br>The conditional statement used a logical AND (`&&`) operator to check if the trimmed title length was simultaneously less than `MIN_TEXT_LENGTH` (2) *and* greater than `MAX_TITLE_LENGTH` (50). Since a string length cannot meet both conditions at once, this validation code block would never execute. | Logic Error | **Changed the operator to a logical OR (`||`)**. This ensures the validation error triggers if the title string length is either too short *or* too long. |

| **2** | `App.tsx`<br>(Line 77) | **Impossible Character Length Validation (Artist)**<br>Identical to the title error, the condition used a logical AND (`&&`) to check if the artist name length was under 2 *and* over 50 characters at the same time, making the check completely non-functional. | Logic Error | **Changed the operator to a logical OR (`||`)** so that entering an artist name outside the acceptable range bounds successfully blocks the form submission. |

| **3** | `App.tsx`<br>(Line 100) | **Missing Upper Boundary Check for Year**<br>The custom validation error alert message claimed that the year must fall between `MIN_YEAR` (1900) and the current calendar year. However, the actual evaluation check only checked if `numericYear < MIN_YEAR`, allowing users to submit future years. | Logic Error | **Added a secondary evaluation condition** (`|| numericYear > currentYear`) to properly enforce the upper boundary restrictions stated in the message. |

| **4** | `App.tsx`<br>(Line 125) | **Missing Upper Boundary Check for Rating**<br>The validation text indicated that the rating must be between 1 and `MAX_RATING` (5). However, the implementation condition only validated `numericRating < 1`, which allowed values higher than 5 to pass through without error. | Logic Error | **Expanded the validation condition** to include `|| numericRating > MAX_RATING` to block invalid rating numbers. |

| **5** | `App.tsx`<br>(Lines 143-150) | **TypeScript Strict Type Mismatch**<br>The code instantiated `temporaryAlbum` with numerical values for `year` and `rating` by wrapping them in the `Number()` constructor. This directly violated the `Album` type interface contract configuration declared at the top of the file, which explicitly expects string values. | TypeScript Error | **Passed clean string variants** using `year.trim()` and `rating.trim()`. This satisfies the compiler constraints without changing the component's underlying structural definitions. |

| **6** | `App.tsx`<br>(Line 152) | **Overwriting Existing State Arrays**<br>The collection hook update was structured as `setAlbums([temporaryAlbum])`. This completely replaces the existing collection array state with a single new item, wiping out all previously entered records every time a new album is saved. | Runtime / Logic Error | **Introduced array destructuring spread syntax** (`setAlbums((prevAlbums) => [...prevAlbums, temporaryAlbum])`). This appends the new entry while preserving the existing database records. |

| **7** | `App.tsx`<br>(Line 162) | **Inverted Collection Filter Deletion**<br>The array `.filter()` method keeps items that return a truthy evaluation. The expression `album.id === id` targeted the exact item intended for deletion. This resulted in keeping *only* the item clicked and discarding the rest of the collection. | Logic Error | **Swapped the strict equality operator** to a strict inequality operator (`album.id !== id`). This preserves all elements inside the array state *except* the one matching the deletion ID. |

| **8** | `App.tsx`<br>(Lines 212-220) | **Incorrect Picker Variable Bindings**<br>The picker setup had two breakdown points: the root component tracked the `title` variable state (`selectedValue={title}`) instead of `genre`, and the mapping iterator assigned the generic hook value to every menu entry (`value={genre}`) instead of assigning the dynamic item string (`value={item}`). This made selection impossible. | Logic / UI Runtime Error | **Re-assigned the parent tracking value** to target the `genre` state hook, and updated the child iteration loop so that each individual entry maps cleanly onto its specific `value={item}` context. |

---

## Testing

1. Invalid Form Submission

Scenario Checked: Attempting to submit empty fields or out-of-bound values.

Testing Steps & Observations:

	• Empty Submissions: Left fields blank and clicked "Add to Favourites." The application blocked the submission and threw the expected validation alerts for each missing element.

	• Out-of-Bound Lengths: Entered a single character ("A") and a string exceeding 50 characters in the Title and Artist fields. The updated logical OR (||) operators successfully caught the boundary infractions and blocked saving.

	• Invalid Numbers (Year & Rating): Entered a year in the future (2030) and a rating of 6. The corrected upper-boundary validation checks successfully intercepted these inputs and displayed the proper boundary warning messages.


2. Valid Form Submission

Scenario Checked: Filling out all form fields with valid, clean entries to ensure proper item creation.

Testing Steps & Observations:

	• Filled in the input fields with standard values (e.g., Title: "Abbey Road", Artist: "The Beatles", Year: "1969", Genre: "Rock", Rating: "5").

	• Upon clicking "Add to Favourites," all internal validations passed cleanly without alerting.

	• The form input fields automatically cleared out and reset to their default empty states, ready for the next entry.

---

## Screenshots

<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 1: Home Screen.*


<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 2: Added to Album.*


<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 3: Validation Error: Enter Information.*


<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 4: Validation Error: For Album Title.*


<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 5: Validation Error: For Artist Name.*


<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 6: Validation Error: For Genre.*


<img width="3170" height="1674" alt="site map" src="https://github.com/user-attachments/assets/6d9ead61-dae3-4451-b91c-c6f456351a73" />

*Caption for screenshot 7: Validation Error: For Rating.*

---

## Conclusion

Analyzing this code revealed how minor conditional oversights, such as using && instead of || or misconfiguring Picker value bindings, completely break input validations and UI controls. Correcting the state management structure showed that utilizing array destructuring spread syntax is critical to prevent new data entries from accidentally overwriting existing records. Fixing the array filter deletion logic demonstrated that applying the correct strict comparison operators is essential to keep state manipulations isolated to a single targeted element. Ultimately, the investigation highlighted that maintaining strict TypeScript type contracts and testing edge-case boundary limits are fundamental to building predictable, crash-free mobile applications.

---

